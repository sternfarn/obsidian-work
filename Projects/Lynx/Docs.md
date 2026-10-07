
# Run

## Start dev server with ai token to enable ai features locally

```bash
AI_COOKIE='token=<token>' npm run dev
```
`<token>` should be the [ai.nexxar.com](https://ai.nexxar.com/) Cookie named  `token`

## Enable Claude code browser access

Update `.playwright/state.json` → `value` with the hippo authsession cookie

or to this:

```bash
LYNX_USER=StefanR
LYNX_PASSWORD=...
```

If it does not work try ```
```bash
export LYNX_USER=StefanR
export LYNX_PASSWORD=...
```

# Accordeon

- **tabacc_selector:** ``.lynx .lynx-acc-trigger``
- **tabacc_type:**: ``acc``
- **Special class to exclude inbetween headline from accordeon:** ``no-tabccordion``

# CMS/FTL behaviour:

- When Lynx invalid or non-existent Lynx block is added in Saturnia, it renders the index before twice. If there is no block before it does nothing.

# Saturnia

**Edit** → optainEditable, enableEditingMode
**...** → performPendingChanges
**Discard** → disposeEditable, resetChanges
**Save** → commitEditable, performPengingChanges

# Regex to replace anchors
Does not work for empty anchors
```
("anchor":.[\S\s]+?"value": ")(.+?)("[\S\s]+?"value": ")(.+?)(")
$1#\L$2$3#\L$4$5
```

# Places

**AutoIds
- https://nexxar.atlassian.net/browse/NXRCMS-4858

**Lynx folder
- https://nexxar.atlassian.net/browse/NXRCMS-4837
- https://nexxar.atlassian.net/browse/NXRCMS-4775?search_id=51f9f684-8371-4f81-86cc-eadb248c9327

**JD einbau
- https://saturnia-staging.nexxar.com/content/clients/fac88808-ac69-4902-9608-16d53d7ac50a/reports/46c147c4-863a-46b6-88dc-8641601b45ca/pages/fc431826-8e39-486f-8c8b-5632d6f555f6/default

**Productive
[√] https://app.productive.io/17342-nexxar-gmbh/tasks/14715107
- [ ] https://app.productive.io/17342-nexxar-gmbh/tasks/14812794

**Geberit indices einbau
- https://hippo-staging.nexxar.com/clients/geberit/ar24/de/nachhaltigkeit/berichtsstandards/fortschrittsbericht-ungc

**Jira
- https://nexxar.atlassian.net/browse/NXRCMS-4605
- https://nexxar.atlassian.net/browse/NXRCMS-4580

**CSS location
- "https://hippo.nexxar.com/binaries/_ht_1731693615323/content/assets/clients/skeleton/ar/de/css/external/lynx.css"