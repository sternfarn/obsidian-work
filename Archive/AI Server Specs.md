# Specification — Lynx AI backend


Requirement levels: **MUST**, **SHOULD**, **MAY** as in RFC 2119.

This document specifies the service, not a particular implementation of it.

---
## 1. Purpose

The goal is to let a user ask an AI to perform editing tasks they would otherwise do by hand.

Lynx is a **client-only static SPA**. It is built on a GitLab runner and mirrored to `htdocs/` over SFTP; no process of ours runs on the web host. It therefore cannot hold an Anthropic API key: anything in the bundle is readable by everyone who opens the app.

This service exists to hold that key and to decide who may spend it.

## 2. Scope

### In scope

- Holding the Anthropic API key
- Authenticating callers
- Forwarding `POST /v1/messages` to the Anthropic Messages API
- Streaming the SSE response back without buffering
- Enforcing model, token, rate and budget limits
- Recording token usage for cost attribution

### Explicitly out of scope

- **Running the agent loop.** The loop runs in the browser, because the Zustand stores it mutates live in the user's tab and hold an editable that user has locked. No server-side loop can reach them.
- **Executing tools.** Tool calls are dispatched by Lynx into its own stores.
- **Building prompts.** Lynx owns the system prompt and tool definitions.
- **Persisting conversations or report content.**
- **Saving or committing to the CMS.** `performChanges` and `commitEditable` remain human-triggered from Lynx.

The service is a dumb, careful pipe. That is a deliberate constraint, not an omission.

## 3. Deployment target

To be defined.

## 4. Authentication

To be defined.

## 5. Interface

The path **MUST** mirror the Anthropic API so the official SDK works unmodified against this `baseURL`.

### `GET /healthz`

Unauthenticated liveness probe. Returns `200` and `{ "status": "ok", "uptimeSeconds": <int> }`. **MUST NOT** disclose configuration.

### `POST /auth/login` — `workbench` mode only

Request `{ "username": string, "password": string }`. Response `200` `{ "token": string, "expiresAt": ISO8601 }`, or `401`.

### `POST /v1/messages`

Requires `Authorization: Bearer <token>`. Body is an Anthropic Messages request.

The service **MUST** override, regardless of what the client sends:

|Field|Behaviour|
|---|---|
|`stream`|forced to `true`|
|`model`|**MUST** be in the configured allowlist, else `400`|
|`max_tokens`|clamped to the configured ceiling|
|`api_key`|stripped|

`messages`, `system`, `tools`, `thinking` and `cache_control` **MUST** pass through untouched, so tool use and prompt caching work normally.

### Errors

JSON: `{ "error": { "type": "proxy_error", "message": string } }`. `429` responses **MUST** carry `Retry-After`. Upstream errors **SHOULD** be relayed with their original status and body so client-side SDK error handling still works.

## 6. Streaming

- The response **MUST** be streamed to the client as it arrives. Buffering the full response before sending **MUST NOT** occur at any layer.
- The service **MUST** set `X-Accel-Buffering: no`.
- Any reverse proxy in front **MUST** disable response buffering (`proxy_buffering off;` for nginx). This is the single most common way the deployment is shipped broken: the stream still works, but the user sees nothing for twenty seconds and then everything at once.
- A time-to-first-byte timeout **MUST** apply to the upstream response _beginning_. Streams **MUST** then be allowed to run long.
- If the client disconnects, the upstream request **MUST** be aborted, so an abandoned tab stops generating billable tokens.

## 7. Limits and cost control

- Model allowlist, `max_tokens` ceiling, per-user requests-per-minute, and a per-user daily token budget **MUST** all be configurable.
- Exceeding a limit **MUST** return `429` with `Retry-After`.
- A separate API key **MUST** be used per environment, each with a spend limit set in the Anthropic Console.
- Token usage **MUST** be recorded per request and attributable to a username.

## 8. Security

- The API key **MUST** exist only in server-side configuration, never in any response, log line or client-reachable surface.
- A client-supplied `x-api-key` **MUST** be ignored.
- CORS **MUST** echo an exact allowlisted origin with `Access-Control-Allow-Credentials: true`. `*` **MUST NOT** be used.
- CORS **MUST** be handled in exactly one layer. If the application handles it, the reverse proxy **MUST NOT** add `Access-Control-*` headers.
- Request bodies **MUST** be size-capped.
- Prompt and response content **MUST NOT** be logged. Cookies, `Authorization`, the API key and any field matching `password|token|secret` **MUST** be redacted structurally rather than at each call site.
- The service **SHOULD** bind to loopback when a reverse proxy terminates TLS.
- The process **SHOULD** run as a dedicated unprivileged user with no capabilities.

## 9. Observability

- Logs **MUST** be single-line JSON on stdout/stderr.
- Each completed request **MUST** emit one line carrying: username, model, input tokens, output tokens, cache read/creation tokens, stop reason, duration, whether the stream was interrupted, and running daily spend.
- Configuration **MUST** be validated at startup, and the process **MUST** exit non-zero listing **every** problem found, rather than failing on first use.

## 10. Operations

- `SIGHUP` **MUST** reload the token store without dropping connections.
- `SIGTERM`/`SIGINT` **MUST** stop accepting new connections, allow in-flight streams a grace period, then exit.
- A configuration change (including the API key) requires a **restart**, not a reload.
- Key rotation **MUST** be possible without downtime, by overlap: create the new key, deploy, verify a real request succeeds, then revoke the old key.
- The service **MUST** be stateless on disk. Losing the host loses nothing but in-memory rate-limit counters.

## 11. Infrastructure requirements

What the service needs from infra, in full:

|Item|Detail|
|---|---|
|Host|One small VM or container. Stateless, no database, no persistent volume. Internal network is sufficient — this is not a public service.|
|Runtime|Node.js ≥ 24, or a container runtime. No other dependencies.|
|DNS|`lynx-api-dev.nexxar.com` first; staging and production later.|
|TLS|A certificate for that name, terminated at the reverse proxy.|
|Reverse proxy|Forwards to the service port with response buffering **off**.|
|Firewall|Inbound 443 from wherever Lynx users are; outbound HTTPS to `api.anthropic.com` and `workbench.nexxar.com`.|
|Secrets|An env file readable only by the service user, mode `0640`.|
|Process supervision|systemd or the equivalent; restart on failure, start on boot.|
|Logs|stdout/stderr to journald or the existing log shipper.|

Resource envelope: single process, tens of MB of memory, effectively no CPU (the work is network waiting). Expected load is a handful of concurrent users.

Blast radius: if this service is down, Lynx continues to work exactly as it does today. Only the AI feature is unavailable. It shares no host, no database and no process with anything existing.

## 12. Constraints and decisions

- **Zero runtime dependencies.** Node built-ins only, so `npm audit --omit=dev` stays clean and the container ships no `node_modules`.
- **Single instance.** Rate limits and budgets are in-process. Running more than one replica makes limits per-replica; the counters must move to a shared store first. This **MUST** be revisited before any horizontal scaling.
- **A request rejected for a disallowed model still consumes a rate-limit slot.** Intentional: it makes hammering the endpoint with junk expensive.
- **`/v1/messages` is a transparent passthrough.** Any authenticated user can send arbitrary prompts and use it as a general-purpose Claude. Accepted for internal staff on an internal network. To tighten, replace the passthrough with a narrow endpoint taking `{ conversationId, messages }` where the server chooses model, system prompt and tool definitions.

## 13. Open questions

1. **`token` or `workbench` auth mode for the pilot?** Both are implemented. `token` involves no password handling and is the easier security conversation; `workbench` needs no manual provisioning.
2. **Will workbench set `Domain=.nexxar.com` on its cookie?** If yes, cookie validation becomes possible and both modes above could be dropped.
3. **Does Nexxar already run Node services anywhere, and how?** Conforming to an existing pattern would reduce this to almost no new operational surface.
4. **Who owns it in production** — this team, or hippo/workbench?

## 14. Acceptance criteria

The service is ready for a dev deployment when all of the following hold:

1. Configuration validation fails closed, listing every problem, on an incomplete environment.
2. An unauthenticated request to `/v1/messages` returns `401`.
3. A request with a valid credential returns `200` with `Content-Type: text/event-stream`.
4. SSE frames arrive incrementally at the client, not batched at the end.
5. A client sending `max_tokens: 999999, stream: false` results in the upstream receiving the configured ceiling and `stream: true`.
6. A client-supplied `x-api-key` never reaches the upstream; the server's key always does.
7. A disallowed model returns `400`; an oversized body returns `413`.
8. Exceeding the rate limit returns `429` with `Retry-After`.
9. Token usage is logged per request, attributed to a username, with no prompt or response content anywhere in the logs.
10. `SIGTERM` drains in-flight streams and exits cleanly; `SIGHUP` reloads the token store without dropping connections.

All ten are covered by automated tests or documented manual verification in this repository.