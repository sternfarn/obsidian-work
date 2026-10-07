# Untriaged browser labels — mobile share is probably under-reported

  

**Status: not actioned. Recorded so it isn't lost.** Found August 2026 while fixing the

`Mi Browser` / `Opera Mini` rename in `modules/core/topics/browser.py` (see the end of this

file). Nothing here has been changed in the code.

  

## How the mobile figure is built today

  

`modules/core/download.py:114` calls Matomo `DevicesDetection.getBrowsers`, keeps `label` and

`nb_visits`, and stores the result as `downloads.json['browser']`. `modules/core/report.py:226`

passes that array into `Browser.__init__`, which does:

  

- `total` = sum of `nb_visits` over **every** label in the array

- `mobile` = the fraction of `total` whose label matches a hardcoded list

  

A label that isn't in the list is therefore still counted in the denominator and silently

treated as non-mobile. There is no "unknown" bucket and no warning — an unrecognised label just

lowers the mobile share.

  

## The labels nobody has classified

  

These appear in the `getBrowsers` response but are in **neither** mobile list in `browser.py`

**nor** either list in `resources/browser.notes`. They are in-app webviews: the browser embedded

inside an app, rather than a browser someone installed.

  

Counts aggregated over the stored `downloads.json` files across all local worktrees. Read the

concentration column before the totals — the totals are misleading on their own.

  

| label | total visits | in N reports | concentration |

|---|---|---|---|

| `Facebook` | 15,707 | 17 | **15,151 of it in a single report** (fresenius SHM25 es) |

| `Chrome Webview` | 11,938 | 138 | the only one that is genuinely widespread |

| `Facebook Lite` | 3,718 | 7 | 3,679 in that same fresenius report |

| `Google Search App` | 2,513 | 21 | spread out; largest single 559 (adidas AR25 en) |

| `Instagram` | 1,208 | 13 | 1,085 in that same fresenius report |

| `LinkedIn` | 965 | 15 | spread out |

| `Douyin`, `WeChat`, `TikTok`, `Line`, `Zalo`, `Threads`, `Viber` | < 800 each | | mostly adidas / vw / dsm-firmenich |

  

So there is really only one broad phenomenon (`Chrome Webview`, present nearly everywhere) plus

one report that took heavy social traffic and skews every total.

  

## What it would cost to count them as mobile

  

Estimated by recomputing the stored `browser` arrays — **not** from a fresh run:

  

- **119 stored reports would change**

- median swing: **+0.003** — i.e. for most reports this is noise

- but a long tail where it is not:

  

```

0.269 -> 0.973  (+0.704)  fresenius SHM25 es       <- 97% mobile

0.141 -> 0.261  (+0.120)  dsm-firmenich IAR25 en

0.293 -> 0.394  (+0.101)  vig AR25 en

0.197 -> 0.279  (+0.082)  fresenius SHM25 en

0.207 -> 0.248  (+0.041)  jerónimo_martins AR25 en

```

  

It would also shift `mobile` expectations in `test_excel.py`, which asserts ~70 of them.

  

## The open question — do not treat the above as measured

  

Whether these labels are mobile is an **inference** from what they mean in Matomo's

device-detector (`Chrome Webview` is Android's WebView component; `Facebook`, `Instagram`,

`LinkedIn`, `Google Search App` are the in-app browsers those apps embed). It has **not** been

verified against our data: the stored downloads carry browser labels only, with no OS or device

dimension to check against. The fresenius `0.973` in particular deserves suspicion before

anyone acts on it.

  

**Suggested way to settle it:** `DevicesDetection.getType` — the same API family already called

at `download.py:114` — returns smartphone / tablet / desktop directly. Comparing it against the

label-list result for a handful of the affected reports above would give ground truth in one

run. Longer term it would remove the need to curate a browser-label list at all, which is the

real fragility here: the list has to be maintained against every Matomo device-detector

upgrade, and silently under-counts whenever it falls behind.

  

## Two side notes on `resources/browser.notes`

  

- It disagrees with the code: it files `Qwant Mobile` and `NetFront` under *web* browsers, while

  `browser.py` counts both as mobile.

- It ends mid-word at `Seznam Br`, so it looks abandoned partway through. It is documentation

  only — `browser.py` is the source of truth.

  

## Related fix already made

  

The same sweep found three entries in `browser.py` that matched **nothing** in current Matomo

data, because the device-detector had renamed them — historical archives come back under the new

name, since labels are resolved at report time:

  

- `MIUI Browser` → `Mi Browser` (661 visits uncounted repo-wide) — **fixed**

- `Opera mini` → `Opera Mini`, capital M (75 visits) — **fixed**

- `Liebao` → now `Cheetah Browser` / `LieBaoFast` — **left alone**, `browser.notes`

  deliberately files Cheetah Browser under web browsers

  

Also fixed: `Firefox Focus` appeared in both `all_mobile_browsers` and `more_mobile_browsers`,

and the nested comprehension counted it once per occurrence, so it was doubled for report years

2020+.