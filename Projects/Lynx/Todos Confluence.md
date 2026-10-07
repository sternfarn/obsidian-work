
>[!info] Confluence
>Do not work on it here but in confluence and tickets

---

## Internal Links

- [ ] **Feature:** Implement anchor link support. *(highest)*

### Update Anchor Links

- [ ] **Feature:** Validate links, maybe when loading the index. If a target is no longer available, mark the link as invalid to indicate that user action is needed. (Merck — a CMS page was removed and was hard to discover.) This feature would also highlight broken links when the index is used from the previous year. *(high)*
- [ ] **Feature:** Internal links should use the page header (h1) as link text. But the navigation title, which is currently used, should still be usable. There should be an option switch. *(high)*
- [ ] **Feature:** Texts should be convertible to links. Sometimes we already have a column with the correct link texts. *(medium)*
- [ ] **Feature:** Copy a link onto existing text to apply the link. E.g. update a prior-year link to this year, then apply it over the newly imported text. *(low)*
- [ ] **Breadcrumbs:** Every part of the breadcrumb should link to its specific target. E.g. "Chapter A > Subchapter a > Page title" — Chapter A should link to Chapter A, Subchapter a to Subchapter a… (Albert) *(offer as option)*
- [ ] **Breadcrumbs:** Option to exclude the front parts of breadcrumbs from being clickable. Only the last part (the actual page) should be linked; the preceding parts should look like plain text. (Albert) *(declined)*
- [ ] **Redirects:** Mark redirects in the link picker dialog and in the content view, to give awareness that backlinks will be missing (redirect pages are not real visible pages, so there can be no backlink). *(high)*
- [ ] **Redirects:** Exclude redirects from breadcrumbs. Otherwise we get "Vorwort > Vorwort". *(medium)*
- [ ] **UX:** Tooltip at links is missing. Add title attribute with link info again. *(high)*
- [ ] **UX:** Empty links should be easier to grab. *(low)*
- [ ] When a text is given a link, all identical texts should get the same link.
- [ ] Option to exclude pre and post from being linked. Offer as a toggle if easy to implement. *(low)*

### Internal Link Picker Dialog

- [ ] Root-level pages are missing. (Telefonica AR25) *(high)*
- [ ] **Feature:** Provide a list of all used links. User can pick from this list to insert links already used elsewhere in the same index. This way, customized links (different title, etc.) are already available. *(medium)*
- [ ] **UX:** Make the link picker window movable. Sometimes it overlaps a description you'd like to see while browsing links. *(low)*
- [ ] **UX:** The link search filters by page title. Extend the filter to also cover chapters and headlines (once headline/anchor support exists). *(low)*
- [ ] **UX:** Also show structureId in the link picker dialog. *(low)*
- [ ] If the user has a structureId, they should be able to search for links by it.

### Internal Link Edit Dialog

- [ ] **UX:** Add a hashtag at anchors automatically if no accordion anchor `?` is used. The hashtag should be visible before the input field to indicate it's always there, so the user can omit it. If typed in the input field, remove it automatically. Normalize old anchors on index fetch. At serialization, add the hash except if a question mark is used. Alternative: make a drop-down with `#` and `?` before the anchor input field, defaulting to `#`. *(high)*
- [ ] **UX:** Sanitize anchor (no invalid characters, spaces, äöü, …). Also disallow uppercase, since Saturnia doesn't allow it either, to avoid mismatches. *(high)*
- [ ] **Feature:** "Change link" should only change the target but keep the titles in place. Currently the whole link is replaced, as if the user deleted it and created a new one. *(low)*
- [ ] **UX:** Chapters and headlines should be part of search and filter. *(low)*
- [ ] **UX:** Document URL should be clickable not only for the first language. *(low)*
- [ ] **UX:** Hide pre and post by default — they confuse some users. Allow them to be shown globally in settings. If the prior-year index uses pre/post, show them by default. *(low)*
- [ ] **UX:** Don't connect anchors by default — languages are usually different. *(low, should be irrelevant after auto anchor support)*

### Update Links

- [ ] **Feature:** Extend "update links" so it not only adapts changed CMS titles but also updates prior-year links to current-year links. Every piece of data of an internal link should be updated via the structureId, since structureIds are the most persistent year-to-year identifier. *(high)*
- [ ] Update links did not work correctly at Geberit. *(high)*
- [ ] **UX:** Update links should have a global "update all" button to avoid clicking "update" for every unique link. *(medium)*
- [ ] **Feature:** Breadcrumb should be part of "update links". *(medium)*
- [ ] **UX:** The "update links" button should be highlighted (e.g. red) to indicate that action is needed when updates are available. *(medium)*

# Editing
## Search and Replace

- [ ] **Feature:** Support regex. Also suggest pre-defined / built-in regexes via a dropdown. *(medium)*
- [ ] **Feature:** Search and replace for custom classes. *(medium)*
- [ ] **Feature:** Make more types of data replaceable: structureIds, visit URLs, … (show a preview of what would be replaced).
- [ ] Advanced search and replace with access to raw data. *(from meeting)*
- [ ] Service links (landing page, download page, …) should also be search-and-replaceable. Currently they are ignored. *(low)*
- [ ] **Feature:** Implement regex replacements — similar to table regex snippets — to enable workarounds and quick fixes for advanced users.
## Custom Classes

- [ ] **UX:** Classes should be addable to columns (every cell of a column, like for icon columns). *(high)*
- [ ] **Feature:** Items like text, internal links, external links, service links, icons, and tables should also support custom classes. It could be necessary to put e.g. `show-for-pdf` or `hide-for-pdf` on links. *(high)*
- [ ] **UX:** Common classes like `pdf-page-break-before`, `show-for-pdf`, etc. should be built in and selectable. *(low)*
- [ ] **Feature:** Introduce a highlight feature (like `<mark>` in TE). Create a standard class for marking: `lynx-mark`, `lynx-note` with an on-brand background color. Or a native setting: mark an item (text, link) and click a highlight button in the toolbar. *(medium)*
- [ ] **UX:** When you change a class name and forget to press OK, it is still changed. This should not be the case — only OK should commit the change. *(high)*
- [ ] **UX:** Adding a class should show a blank input field, not what was entered before. *(low)*

## Texts

- [ ] **UX:** `Alt+Enter` should also insert a new line, not only `Shift+Enter` — users are used to this from Excel. *(high)*
- [ ] **UX:** The text editing input field should have HTML syntax highlighting since it often contains `<sup>`, `<br>`, etc. *(low)*
- [ ] **Feature:** Split texts with line breaks into separate paragraphs. (OMV IRO) *(medium)*
- [ ] **UX:** Add a "delete empty text boxes" function — even after the upload fix, these may still appear in prior-year indices. *(medium)*
- [ ] **UX:** For consistency, copy and paste should also be available in the right-click context menu, not only as shortcuts and in the toolbar. *(low)*

## Footnotes

- [ ] **Feature:** Accessible (A11y) footnotes. *(medium)*

## nbsp / nowrap

- [ ] **Feature:** Let users define a regex pattern (or pick from built-in defaults) for terms that should automatically be wrapped in `<span class="nowrap">`, to prevent texts like "ESRS S1" from breaking across lines. Or offer manual control with a few predefined patterns in search and replace. *(medium)*
- [ ] Wrap replacement hyphens with non-breaking hyphens. (JF)
## Merged Cells

- [ ] Make merging cells work like in Excel: select multiple cells and hit a merge button.
- [ ] What happens if a colspan is in place and then a column is deleted? Should be prevented with a warning, or ideally handled gracefully without causing issues.
- [ ] Span should only be possible if the target cells are empty; otherwise show a notification. (Jo) *(medium)*

## Headlines

- [ ] **Feature:** Make headlines changeable from h2 to h3, caption, etc. — just by setting the type directly, without needing to manipulate the hierarchy. Implement h1/h2/… buttons in the toolbar that set the type for the selected headline(s). Technically solved by making the underlying data structure flat. *(high)*
- [ ] **UX:** The edit icon on empty headlines (needed to grab them) is missing on lower-hierarchy headlines. (HHLA GRI) *(medium)*
- [ ] **UX:** Headlines should support line breaks so they can span multiple lines. Currently requires manual `<br>`. *(low)*
- [ ] **UX:** Sticky headlines? *(low)*

# Configuration

## Upload / Download XLSX

- [ ] Empty cells should not get empty text items. *(high)*
- [ ] Import XLSX tries to use "reimport" when the structure has not changed (only content, e.g. translations) to preserve all information (classes, column widths, …). But it currently does not detect if columns are added, only rows. Fix this to prevent unexpected behaviour. *(high)*
- [ ] **UX:** At upload, handle a few more feedback messages for common misformats in Excel files. (Problem files are already prepared.)
- [ ] **UX:** Include client and report names in the Excel download. (Albert)
- [ ] **Feature:** Alternative to XLSX upload: allow pasting tab-and-newline-separated text into Lynx (like pasting into Confluence tables or Excel). This should create all needed cells and text items on the fly when nothing is there. If something is already there, it should update existing items (in the current language).
- [ ] **Feature:** Implement an advanced Excel upload that creates internal links from specific columns that already contain link texts, structureIds, and anchors. Necessary metadata like the ID can be added implicitly at upload as usual. Links will not have full functionality like breadcrumb support and "visit" (in Lynx, not CMS), since things like chapter and documentUrl are missing. Discuss with Mario first to understand exactly which info was in the Sandvik Excel file. *(high)*
- [ ] **Feature:** Allow re-dropping an XLSX onto an existing index. *(low)

## Settings Drawer

- [ ] **UX:** Give the `swipe-info` index class as a default. This enables the FED "Swipe to Explore" hint. *(high)*
- [ ] **UX:** Add `wide` as a default as well? *(low)*
- [ ] **UX:** The index class has no apply button, but the breadcrumb does. Make it consistent. *(low)*

## Split Index

- [ ] **Feature:** Re-implement split index — this has to be technically different from last time because of blocks. Make insertable separators between any row to indicate split points. Split fragments will be saved as individual blocks. These blocks can be embedded in the CMS where needed (needed by VW and Telekom). The unsplit "big" index can also be embedded (Telekom has both). The big index is the source of truth; saving also updates all split blocks. Split blocks are read-only to avoid conflicts with the source index. *(high)*

## Backlinking

- [ ] HTML tags should be stripped from `backlinking.json`. `<`, `>`, and `/` are already excluded by sanitization, but whole tags like `<nobr>` should also be excluded. Example: `"name": "E2 Umweltverschmutzung<sup>b</sup>"` — remove the `<sup>`. (BASF, Jeronimo, …)
- [ ] **Feature:** Update backlinking automatically on save. No need for manual upload via CMS Editor.
- [ ] **UX:** `backlinking.json` should have a cleaner name — the current one has a very long suffix. (Albert)
## Stylesheet

- [ ] **PDF:** Remove content filter headline classes only at the PDF stylesheet. Maybe add a toggle to turn off PDF modifications. Reason: PDF classes are different.
- [ ] **Paragraph:** Add this to default (Merck)? `.lynx .paragraph+.paragraph { margin-top: 0px; }`
- [ ] **Link:** By default, add `.lynx` to the `.link` CSS selector to overwrite the link content filter class. (Beiersdorf)
- [ ] **Link:** Add "border styling" to the default stylesheet and stylesheet UI. (Beiersdorf)
- [ ] **List:** Add list styling to the default stylesheet and stylesheet UI. (dsm-firmenich)
- [ ] **List:** Lists also need a styling option.
- [ ] **Feature:** WYSIWYG styling — an index style preview where you can directly click on elements to style them.
- [ ] **UX:** When the accordion is fully expanded, typing is slow.
- [ ] **UX:** Add `.lynx a:visited` to the default stylesheet without a color assignment, and add it to the UI with a note that it can save time when testing links. (Albert)
- [ ] **Feature:** Implement versioning for stylesheets.
- [ ] **Default:** Give inbetween columns a min-width of e.g. 8 px (like OMV) to prevent collapse on narrow screens, since the gap is only percentage-based.
- [ ] dsm-firmenich stylesheet needed `"width":` to override a media query setting that reduced `li` width. Consider making `width: auto` the default.
- [ ] **Default:** Lynx margin top. (CPChem)
- [ ] Horizontal padding on `td` makes `padding: 0px` necessary for in-between cells (BLG, CPChem…). Find a solution for easily switching between the two variants.
- [ ] Last paragraph usually needs `.lynx-table__cell > *:last-child { margin-bottom: 0px; }` (Sandvik has `.lynx p:last-child { margin-bottom: 0px }` but many others use the first rule).
- [ ] When `td`s get horizontal padding, in-between cells need to override it back to 0: `.lynx-table__row--thead .lynx-table__cell--in-between, .lynx-table__row--tbody .lynx-table__cell--in-between { padding: 0px; }`.
- [ ] **Add:** Headline border bottom.
- [ ] **Add:** Bechtle needed `.lynx .lynx-row__link` instead of just `.lynx-row__link` to override the default CMS link styling. Can this be added for all, or is it destructive? *(low)*


# Navigation

## Save / Lock / Session

- [ ] Autosave draft every n seconds. *(medium)*
- [ ] The "Error" message appears more often than it needs to, and does not go away when the connection was only briefly interrupted. Instead of showing an error message, display a modal that allows the user to re-login — enabling re-authentication without a page refresh, preventing loss of unsaved work. Already implemented, but only when clicking the Avatar. Nobody sees it there. It needs to pop up automatically if the session is dead. *(high)*
- [ ] When saving, users occasionally see a message indicating that the index is locked by themselves. Additionally, the scroll position is lost. Both should not happen. When this happens on a PDF stylesheet the user might not notice that after this wrong lock warning, the first stylesheet is selected. *(medium)*
- [ ] Implement read-only mode so that an index can be viewed even if it's locked. *(low)*
- [ ] When closing the browser while on the index, there is a browser warning meant as a reminder to close the index (navigate back). But it is misleading since the browser message can't be modified and always says "unsaved changes might be lost", which is the wrong message. Remove this warning. Only keep it when work is truly unsaved, which already works.
- [ ] Auto-unlock (kick user from index) after 2 hours of inactivity and no unsaved changes. This needs to happen on the server, not in Lynx, because when Lynx is closed it's closed, but the server still runs.


## Report Page / Index Overview

- [ ] **UX:** Make the list of indices sortable (report-scoped options node). *(low)*
- [ ] **UX:** Add a "View in CMS" button to the overview so the user can navigate there even if the index is locked. *(low)*


## Dashboard

- [ ] **UX:** "Recently used" resets when it exceeds the max count. Instead, it should just drop the oldest entries. *(medium)*
- [ ] **UX:** "Recently used" should get more space to show more entries. *(low)*
- [ ] **UX:** When an index is deleted it still appears in "recently used". *(low)*
- [ ] **UX:** "Recently used" and "Continue with" should show dates. *(low)*
- [ ] **UX:** Use the editable fetch time to show an overview on the dashboard of who is currently working on which project. *(low)*

## Navbar

- [ ] **UX:** The index select dropdown at the top does not update its index list after adding an index.
- [ ] **UX:** All buttons should have tooltips/popovers with a name or explanation. *(medium)*
- [ ] **Feature:** List and bold toggles should also work for multiple selections.
- [ ] **Feature:** Implement cut, and make copy and insert work properly. Currently they are just placeholders.
- [ ] **UX:** The unsaved changes indicator (asterisk) should detect when the user undoes back to the last saved state. *(low)*
- [ ] **Feature:** Make the remaining toolbar buttons work: text align left, right, center. The toggles should add/remove predefined utility classes (e.g. `.align-left`, `.align-right`) which are appended to the Lynx stylesheet automatically.
- [ ] **Feature:** Allow setting borders via toolbar buttons for styling text tables. Border 1, Border 2, … styles are defined in the stylesheet and should be immediately visible.
- [ ] **UX:** The second and third navbars could be combined into one to save vertical space. Make buttons responsive: omit text on small screens, show it as a popover on hover. This would also look more app-like and less website-like. *(low)*
- [ ] **UX:** "Close all" accordion button keeps saying "close all" even after the user has closed everything manually. *(low)*
- [ ] **UX:** Language switch click area is too small — clicking the gap between the two language labels should also toggle. *(low)*
- [ ] **UX:** Versions overview should re-render after save so the new version is immediately visible. *(low)

## Saturnia

- [ ] **UX:** Saturnia should deep-link directly to a Lynx index. This could drive more PM or even client usage of Lynx. Lynx may need routing changes since the client name is currently part of the route, but Saturnia seems to work only with full report names and reportIds. *(medium)*
- [ ] **UX:** Saturnia should not display "Stylesheets" in the "browse index" list. A stylesheet is never added as a block — it only appears there for technical reasons (stylesheet data is also an index node to enable locking and versioning). *(low)*

## Shortcuts

- [ ] **UX:** Modals should support the Enter key to confirm. *(low)*
- [ ] **UX:** Select links with keyboard keys. *(low)*
- [ ] **UX:** Every edit should be confirmable with Enter. *(low)*
- [ ] **UX:** Show modifier key hints — e.g. when Ctrl is held, underline internal links or change cursor to a pointer. *(low)*
- [ ] **UX:** Select multiple cells with mouse click-and-drag or click + Shift+click (like in Excel). *(low)*
- [ ] **UX:** Navigate through cells with arrow keys and multi-select with Shift (like in Excel). *(low)*
- [ ] **UX:** Delete key should clear cell content from all marked cells. *(low)*
- [ ] **UX:** Ctrl+C and Ctrl+V should also work on cells. Currently they only work for items and paragraphs. *(low)*
- [ ] **UX:** Ctrl+S for save. *(low)*

# Other

## General

- [ ] **Feature:** Implement "copy index" and "copy all indices" from another report (e.g. previous year). *(high)*
- [ ] **Feature:** Replace the three views (Structure / Columns / Content) with a unified view. Don't replace them right away — first create a fourth view while the old ones still work. Once the new view is solid, remove the others. A single view lowers the barrier for structural modifications and is more intuitive for new users. *(low)*
- [ ] **Feature:** Implement an auto-link feature that tries to automatically create links by matching texts with CMS page titles (or headlines) and replacing them with links. Can be used on single texts or whole columns; user must review the links afterwards. *(low)*
- [ ] **Feature:** Automate the `no-tabaccordion` class (FED accordion feature needs this class to stop the accordion from being greedy). (Geberit)
- [ ] **Performance:** To reduce index first-paint loading time, introduce lazy rendering by loading only what's visible on screen first. Note: browser search will not find items that are not yet painted. *(medium)*
- [ ] **UX:** Keep the current selection visible after editing a link or text so the user can see what was just changed. *(low)*
- [ ] **UX:** When toggling a column to hidden, its width should automatically be set to 0. *(low)*
- [ ] **Feature:** Support multiple header rows, not only single-line headers. Generally consider complex headers with merged cells for text tables. *(medium)*
- [ ] **Feature:** Add a new row type rendered as a simple `div` in the CMS. Any HTML can be inserted — enables workarounds and quick fixes for advanced users. *(low)*
- [ ] **UX:** Icons should be placeable next to other items, not only under other icons. (Tables are always block elements and excluded.) *(medium)*
- [ ] **Feature:** Make Lynx downloadable in the CMS like table XLSX downloads. Lynx creates a styled XLSX per index and language on the fly and sends it via a WB endpoint to the CMS (like stylesheets). A toggle in Lynx (downloadable / non-downloadable) enables a download button in the CMS. Additionally, an explicit button downloads the styled XLSX so it can be manually improved and re-uploaded to override the automatic file. (OMV) *(low)*
- [ ] **UX:** Bilingual annotations for separate per-language checks and language-specific notes? *(low)*
- [ ] **UX:** Empty lines are too slim. *(low)*

## More Responsive in CMS

- [ ] Grid instead of table. Check compatibility with Prince… *(medium)*
- [ ] Consider the mobile render method discussed previously, where the header repeats. *(medium)*
- [ ] **Feature:** Implement special cell classes (easily toggled from toolbar buttons) that define how the cell breaks on mobile — especially useful for large indices or text tables.
