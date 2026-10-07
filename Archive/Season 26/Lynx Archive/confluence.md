### Links
Implement anchor link support. (high)
Tooltip at links is missing. Add title attribute with link info again. (fast)
Texts should be convertable to links. Sometimes we have already a column with the correct link texts. (high)
link auf bestehenden text draufkopieren um verlinkung reinzubekommen. Z.B. VJ-Link updaten auf diesees Jahr. Dann über neu importierten Text hauen. (medium)
Empty links should be easier to grab (low)
Validate every link when loading the index. Check against pages. If a structureId is not available anymore, mark the link as invalid, f.e. red. (low)
Breadcrumbs: Every part of the breadcrumb should link to the specific targt. F.e. "Chapter A > Subchapter a > Page title" → Chapter A should link to Chapter A, Subchapter a should link to Subchapter a...  (Albert) (low)
Breadcrumbs: Option to exclude the front parts of Breadcrumbs from being clickable. Only the last part of the Breadcrumb, the actual page, should be linked. The Breadcrumb parts before should look just like text.  (Albert) (medium)
Redirects: Mark redirects in the link picker dialog and in the content view (To give awareness that backlinking will break). (high)
Redirects: Exclude redirects from Breadcrumbs. Otherwise we have Vorwort > Vorwort (medium)

### Link picker dialog
Bug: Root level pages are missing. (Telefonica AR25) (high)
Provide a list of all used links. User can pick fom this list to insert links that are already used elsewhere in the same index. This way, customized links (different title, ...) is already available. (low)
Make the link picker window movable. Sometimes it's over an description that you would like to see while browsing links. (low)
Die Link suche filterd anhand der Seitentitel. Erweitere den Filter auch auf Chapter und headlines (sobald es Headline/Anker support gibt) (low)
Im link picker dialog auch structureId anzeigen (low)

### Internal link edit dialog
Add hastag at anchors automatically if no accordeon anchor "?" is used. The hashtag should be visible before the input field, to indicate it's there anyway, so that the user can ommit it. If its' typed in the input field, remove it automatically. Normalize old anchors already on fetch index. At serialization add the hash, except if a question mark is used. Alternative, make a drop down selection input with # and ? before the anchor input field. Default is # (high)
Sanatize anchor (no invalid characters, space, äöü, ... ) Also don't allow uppercase, since saturnia also doesn't allow it, and to avoid mismatches. (high)
"Change link" should only change the target, but keep the titles in place. Currently the whole link is changed, as if the user would delete the link and create a new one. (low)
Also chapters and headlines should be part of search and filter. (low)
document url haben zum klicken nicht nur für die erstsprache. (low)
pre und post ausblenden bei default, verwirrt manche Leute. In settings global einblenden können. Falls VJ Index Pre post verwendet ist es default eingeblendet. (low)
Anker default nicht verbinden, meisetns sind die sprachen verschieden. (low, shold be irrelevant after auto anchor support)

### Update links
Update links should be extended so that it does not only adabt changed CMS titles but also to update last year links to current year links. Every data of an internal link should be updated via the structureID, since StructureID's are the most persistent year-to-year data of pages. (high)
update links did not work correctly at geberit. (high)
Update links should have a global button to avoid clicking "update" at every unique link (medium)
Breadcrumb should be part of "update links". (medium)
The "update links" button should be highlighted (e.g. red to indicate that action is needed) if updates are available. (medium)

### Split index
Implement split index again, this has to be technically different then last time because of blocks. Make Seperators insertable between any row to indicate where the index will be split. Splittet fragements will be saved as individual blocks. These blocks can be embedded in the CMS where needed (VW, Telekom). Also, the unsplitted "big" index can embedded (Telekom). The big index is the sorce of truth, saving additionally updates all splitted blocks. Splitted blocks are read only to avoid conflicts with the big source index. (high)

### Custom classes
Adding a class should be blank and not not show what was in the input field before.
Classes should be addable to columns (ever cell of a column)
Items (Text, Int. links, ext. links, service links, icons, tables) should also support custom classes. It could be neccessary sometimg to put f.e. show-for-pdf or hide-for-pdf on links.
Common classes like pdf-page-break-before, show-for-pdf and co. should be built in and selectable.
Highlight einführen (wie <mark> beim TE). Standard class anlegen fürs markieren. lynx-mark, lynx-note mit einer on-brand hg farbe. Oder ein natives Setting: item (text, link) markieren und in der toolbar oben einen highlight button machen.
When you change a class name and forget to press ok, it is still changed. This should not be the case. Only ok should commit the change.

### Report page / index overview
Make index overview on report page sortable. (report scoped options node)
View in CMS button schon in der overview damit man falls der index gesperrt ist trotzdem hinspringen kann

### Settings Drawer
index klassen vorfertigen. wide, swipe-info (default geben)
The index class has no apply button, the breadcrumb does. Make it consistent. (low)

### Saturnia
Saturna should link to index. This could lead to more PM or even Client useage of Lynx. It should be a deep link directly to an index. Maybe Lynx needs routing changes for this, because now the client name is part of the route, but Saturnia seems not to work with client names but rather full report names and reportIds only. (medium)
Saturnia should not display "Stylesheets" in the "browse index" list. A stylesheet is never added as block. The reason it's listed there is only technical, because stylesheet data is also an index node editable to enable locking and versioning. (low)

### Stylesheet
PDF: Remove content filter headline classes only at pdf stylesheet. Maybe add toggle at stylesheet to toggle away pdf modification. Why? PDF classes are different.
Paragraph: Add this to default (Merck)? .lynx .paragraph+.paragraph {  margin-top: 0px; } https://lynx.nexxar.com/#/Merck/7060788a-6602-45d4-8197-d6c0179552ef/77ceb9f5-c7a1-4d4b-b3c7-29aa6144b6c6
Link: By default, add ".lynx" to .link css selector to overwrite the link content filter class. (Beiersdorf)
Link: Add "border styling" to default stylesheet and the stylesheet UI (Beiersdorf)
List: Add list styling to default stylesheet and stylesheet UI (dsm-firmenich)
List: List also needs styling possibility
WYSIWYG Styling. Index stlye preview where you can direclty click on elements to style them.
Stylesheet: When all is expended typing is slow
.lynx a:visited ins standardstyleseet ohne farbzuweisung und ins ui, mit zusatz das das beim linktesten zeit sparren kann. (Albert)
implement versioning for stylesheets
inbetween cols eine min width von sagen wir 8px geben wie bei omv, weil sonst rutchst es zusammen wenn bilschirm schmal ist weil der gap ja nur in prozent angegeben ist.
dsm-firmenich stylesheet needed "width": to override a media query setting that reduced li width. Consider make width: auto default. But still, it also needed article and the media query to override.
.lynx margin top (CPChem)
Horizontal padding on td makes padding 0px necessary for in-between cells (BLG, CPChem...).
Last paragraph usually needs .lynx-table__cell > *:last-child {margin-bottom: 0px;} (Sandvik has .lynx p:last-child { margin-bottom: 0px } but many others have the first one).
When tds get horizontal padding, the in-between cells need to override that back to 0: .lynx-table__row--thead .lynx-table__cell--in-between, .lynx-table__row--tbody .lynx-table__cell--in-between { ......  padding: 0px;}.
Headline border bottom.
Bechtle needed .lynx .lynx-row__link statt nur .lynx-row__link to override the default cms link styling.

### Upload/Download XLSX
Empty cells should not get empty text items.
Export import implizitly uses "reimport" by default. This is good for translations, but bad if more things are added. (OMV) Consider a seperate "import translations" button that can be used when the Excel is structurally unchanged. (OMV)
xlsx reindropen (low)
Handle a few more errors. Examples of excel files with specific errors are already stored (Stefan local)
Im excel download kunden und report namen dazuschreiben (Albert)
Make alternative to upload excel: Just make tab- and new line seperated text pastable into Lynx (like pasting text in confluence tables or excel). This should create all needed cells and text items on the fly when nothing is there. If something is there already, it sould update existing items (in the current language)
Impelemnt an advanced excel upload that creates internal links from specific columns that already have linktexts, structureId and anchors. Necessary metadata like the id can be added implicilty at upload like usual. But the links will not have full functionallity like breadcrumb support and "visit" (in Lynx, not CMS), since things like chapter and documentUrl (cms.nexxar.com/...) are missing. Discuss it with Mario first to understand exaclty which info would have been there already in the excel file. (Sandvik)

### Save/Lock/Session...
Autosave draft every n seconds. (medium)
The "Error" message appears more often then it needs to. The session poll interval is too hig, and also the message does not go away when the connection was only shortly interrupted. Better, dont just show a error message in the first place, but display a modal that allows the user to re-login. This enables re-authentication without a page refresh, preventing loss of unsaved work. It's already implemented, but only when clicking on the Avatar. Nobody sees it there. It needs to pup up automatically if the session is dead. (high)
When saving, users occasionally see a message indicating that the index is locked by themselves. Additionally, the scroll position is lost. Both should not happen. When this happens on a pdf stylesheet the user might not notice that after this wrong lock messae warning, the first stylesheet is selected (not the pdf stylesheet andymore) (medium)
Implement Read only so that an Index can be viewed even if it's locked. (low)
When closing the browser while beeing on the index, there is a browser warning. The warning is meant as  a reminder to close the index (navigate back). But it is missleading since the browser message can't be modified and it always says "unsaved changes might be lost", wich is the wrong message. Better remove this warning. Only keep it when the work is really unchanged. This works nice already.
Auto unlock on the server after 2 hours of inactivity and no unsaved changes are in place.

### Nav bar
Index select dropdown at the top does not update it's index list after adding an index.
All buttons should have tooltips/pop over with name or explenation of what the button is about. (medium)
List and bold toggles should also work for multiple selections
Implement cut and make copy and insert work. Currently it's just a placeholder.
Unsaved changes indicateion (Asterisk) should detect when user does undo to the state where it was last saved (low)
Make the other buttons in the toolbar work: Text alin left, right, center. The toggles should add/remove utility classes on the selected cells. (pre defined classes like, .align-left, align-right, that will be appended to the lynx stylesheet automatically).
The second nav bar and the third nav bar could easily be combined to one navbar to save vertical space. They have lots of white space. Just make the buttons responsive: They should ommit text on small screens and instead show text as popover when the button is hovered. This would also look more app like and less website like, since Apps do not have such huge whitespace heavy headers, only websites do. (low)
language switch click area ist zu klein. Wenn man auf den Leerraum zwischen den beiden sprachen klickt soll es auch umschalten, nicht nur wenn man eine Sprache erwischt. (low)
Recently used colors does not work (low)
Borders mit buttons in der toolbar setzen können damit man z.b. text tables stylen kann . Border 1, border 2, ... styles sind dann im Stylesheet definiert. Soll dann aber auch gleich sichtbar sein. Damit es richtig aussieht.
"Close all" accordeon-button keeps saying "close all" even if user closed everything manually (low)
"...to enable quick access in the CMS" → "...to enable quick access to the CMS"
"Report page" → "Back to report page". Otherwise it seems like you can "report" something.

### Texts
alt+enter soll auch new line machen, nicht nur shift+enter, weil man ist es vom Excel so gewohnt. (high)
Text editing input field should have html syntax highlight because it often cntains <sup>, <br>... (low)
Feature: Split texts with line breaks into paragraphs (omv iro). (medium)
Function "delete empty text boxes" machen. Weil auch nachdem upload gefixed ist, wird das vom VJ noch manchmal drin sein. (medium)
For consitency, Copy and paste should also be in the context menu (right click), not only available as shortcut and in the toolbar (low)

### Dashboard
"Recently used" resets when it exceeds max num. Instead, it should just loose the older entries. (medium)
"Reently used" should get more space to show more entries. (low)
When index is deleted it still appears in "recently used" (low)
"Recently used" and "Continue width" should have dates. (low)
How long does it take to fetch all editables that are currently in work. Use this information on the Dashboard to make an overview of who is currently working on wich project. (low)

### Footnotes
Footnote text changes are currently not undoable but should be. (high)
Fußnotenzahl ist mittig ausgerichtet → oben ausrichten. (high)
A11y Fn's (medium)

### Shortcuts
Modals should support enter key to press ok. (low)
Select links with keys. (low)
Every edit should be confirmable with enter key. (low)
Modifier info anzeigen. Wenn man strg gedrückt hat interne links unterstreichen oder cursor zu hand werden lassen usw. (low)
Select multiple cells with mouse click and drag or with click shift click (like in excel). (low)
navigate through cells with arrow keys, and multiselect with shift (like in excel). (low)
Delete key should delete cell content from all marked cells. (low)
strg+c and strg+v should also work on cells. Now it works just for items and paragraphs (multiple items in a line) (low)
strg + s for save (low)

### Search and Replace
Support Regex. Also suggest pre defined / built in regexes via drop down. (medium)
Search and replace for custom classes (medium)
Make more types of data replaceable: structureIds, visit urls, ... (low)
Impelemnt regex replacements that run as last step on save, right after the serialized JSON is created and just before it is sent to the Server. This would enable workarounds and quick fixes for advanced users.
Servicelinks in search and replace should also get their own toggle to be replaceable. Now they are ignored. (low)

### nnsp/nowrap
User should be able to define a regex pattern for terms that should automatically get wrapped by a <span class="nowrap">. F.e. to prevent texts like "ESRS S1" and similar ones from breaking into new lines. Or make it simpler and just add a few pre defined patterns to search and replace. (medium)
Bei ersetzungs bindestrich einen nonbreak hyphen rundumhauen (JF)

### Merged cells
Make merging cells like in Excel, where you can select multiple cells and then hit a merge button.
Was passiert wenn man colspan in place hat und dann column löscht? sollte verhindert werden mit hinweis oder noch besser einfach so handeln dass es keine Probleme verursacht.
Merge cells: span soll nur möglich sein wenn kein inhalt drin ist, sonst notifaction (Jo)

### Responsive
grid instead of table
Consider the mobile render method we once talked about, where header repeats.
Impmlement special cell classes (that can be easily toggled in with buttons in the tool bar), that define how the cell breakes on mobile (especially good for a huge index or text table)

### Headlines
Make headlines changable from like h2 to h3 or caption and so forth. This should be possible just by telling the healine what it should be, instead of needing to play with the hierachy. Implement h1 h2 ... buttons in the toolbar which will set the type for the selecte headline (or multiple selected headlines) technically solve this by making the underlying data structure flat. This has an advantage or other needs too.
Sticky?
The edit icons which is at empty headlines to be able to grab them, is missing in lower hierarchy headlines (hhla gri)
headlines sollte nwenn möglich auch umbrüche anzeigen, also über mehrere zeilen gehen können

### Backlinking
Html tags should be removed in backlinking.json. < and > and / is already excluded by sanatization. But exlcude whole tags, like <nobr>. Or Example: "name": "E2 Umweltverschmutzung<sup>b</sup>", sup weg (basf) 
Backlinking.json needs to handle icons in the first 
Backlinking.json should have a nicer name (Albert)

### Initial setup
Implement "copy index" and "Copy all indices" from another report (f.e. previous year).
Implement auto link feature which tries to automatically create links from texts. It tries to match texts with CMS page titles (or even headlines) and replaces texts with links. This action can used at single texts or whole columns. The user needs to check the links afterwards.

### Other
Automate no-tabccordion class (FED Accordeon feature needs this class to stop the accordeon from beeing creedy) (Geberit)
When toggle visibilty to hidden, it's col width should be updated to 0.
To reduce index first paint loading time, introduce lazy rendering by loading only whats visible on screen first. attention, browser search will not find them if the are not painted to the screen. (medium)
Wenn markierung vohanden bleiben würde nachdem man markiert hat, ODER noch besser ein highlight oder effekt drauf ist auf das was man gerade bearbeitet hat wärs besser zu sehen wo man gerade was gemacht hat.
Versions overview should rerender after save so that new version is imeditally visible, not after refresh. (low)
Support multiple headers, not only one line headers. Genereally consider complex headers with merged cells. Some text tables will need them (medium)
Add new row type that will be rendered es simple div in the CMS. Every html can be inserted. This enables workarounds and quick fixes.
Make Lynx downloadable in the CMS, just like table xlsx downloads. When a "create downloadfile" button is pressed, Create a styled xlsx per language on the fly and send it via a wb enpoint (ask for it) to the cms (like stylesheets). and lynx itself can toggle in a dl button. that will download the file in the cms. (low)
Annotations Zweisprachig für seperate checks und sprachspezifische notes?
Icon should be placeable next to other items as well, not only under icons (table not, table is always a block element)
Put a single table line at the very bottom. In the CMS it will be part of the preceeding table, even if this is nested. It was not reported yet, but it could happen. Adust serialization logic to only wrap the row if it's a direct sibling.
Empty lines are to slim (low)
