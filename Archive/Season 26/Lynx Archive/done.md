Upgrades:
[√] Vite update
[√] AUDIT MUSS WIEDER REIN
[√] npm update
[√] react update test
[√] major upgarde remaining packages that make sense
[√] install react compiler
[√] remove manual memoization and test

Reinstate:
[√] The login box is on top of the screen when dev tools is open. Move to center.
[√] log into wb
[√] Send stylesheets to cms
[√] Paste config wieder einbauen
[√] Save
[√] redo normal ouput to incorporate changes (multi lang anchor change needed?)
[√] Cannot visit links of prev year configs 
[√] One output language
[√] acc at structural
[√] Special links: crud service links
[√] Special links: Serialize correctly
[√] Special links: Detect service pages in config normalization and apply correct format
[√] Show Versions
[√] Restore Version
[√] Get wb cors for staging, afterward comment in wb login and session again https://nexxar.atlassian.net/browse/WORKBENCH-847 -> Ticket is done, test
[√] Revalidate links: bei revalidate links structureId anzeigen.
[√] Revalidate links: Revalidate links: Wenn new cms title leer ist wurde mit dieser structure id wohl keine page mehr gefunden, dann soll es nicht möglich sein den linktext auf "" upzudaten. 
[√] Revalidate links: Test bei lindt sr24 gri
[√] Bell icon in nav that opens revalidate links dialog
[√] Browser close warning: Make hasUnsavedChanges store flag
	[√] check on other browser
[√] Unwrap
[√] add custom internal links for unexpected service pages -> Implicilty done with editable servce links

New:
[√] Paste item on line should insert below line
[√] Paste line on item shoul insert below item (invisible line)
[√] Login to WB and Hippo seperatly, in case someone just changed the WB password. Or external user has also not necessary the same WB password, right?
[√] internal link beachtet jetzt auch id. verschiedene id mit gleichem linktext ist trotzdem ein berschiebender link
[√] Edit Anchors uniquly > Edit to unique linklist > Done with the anchor extension in the unique internal links list
[√] View in CMS needs to be saved
[√] Option to show plain links

Tests of non-block version:
[√] compare outputs (and changes) in cms between prod and dev/staging
[√] anchor
[√] test new links
[√] test old links
[√] test anchorlinks
[√] check bold
[√] lists
[√] bold and list at the same item -> list wins
[√] test hide cols in cms -> Works. Hidden header is still in output.json though, but is not visible in CMS.
[√] test row class
[√] test cell class
[√] test index class
[√] test unique row ids
[√] test if line breaks at texts are correct
[√] Serialize module can't handle linline table items or intline lists. Tables and texts of type list must always have their own line. Handle this in UI. -> table/list wins over other inline texts. is ok. I have also put this to nice to have to prevent in in UI
[√] Hardcore compare outputs
[√] service links in cms
[√] service links with backlinking -> Servicelinks are successfully ignored
[√] service link in download xlsx -> Are shown correctly as text in plain text download, and inside json with normal download
[√] service link with search and replace -> are ignored, which is ok for now, but I added it to nice to have
[√] Test CSS compiler

Branches:
[√] from main make "final-config-version-with-isolated-stores" to backup the report level application.
[√] from staging make "final-config-version-with-single-store" to backup the report level application.
[√] Continue with staging. Merge blocks into staging

Blocks Restructuring:
- [x] "Edit" und "Done" button. Edit performed editable. Save performed changes, committed und gleich wieder editable. Done disposed das editable.
- [x] Browser save warning, when index is not closed
- [x] How to change nodeName? Not possible
- [x] Consider deploy the ReLogin fix that is currently only on staging to old version (main and production)
[√] Move fetch config to <reportId>/data
[√] Create new store: IndexNodeId
[√] Mock indexNode flat list fetch on ReportPage
[√] Restructure Serialize
[√] Disable save
[√] Remove Split index from serialize.
[√] Remove Split index from data structure.
[√] Remove Split index from and UI.
[√] Upload
[√] Handle usedColors
[√] Support fetching old config, maybe in hidden route
[√] Mock handle stylesheets
[√] Search for "Config"
[√] Search for "useConfigState"
[√] Make IndexNodeDataPage accept data and update indexNodeStore
[√] All config actions must be updated (configState)
[√] Stylesheet store
[√] Stylesheet actions from indexNodeStore to Stylesheet store
[√] mock fetch stylesheets
[√] save button state feedback
[√] save needs to update asterkix at commit success
[√] Dann eventuell eine convenience automatismus dass es beim laden gleich von selbst auf edit geht wenn frei ist.
[√] Rights check darf nicht nur auf Report page sein, weil was ist wenn jemand mit einem deep link direkt auf den index kommt. Lieber klassisch machen.
[√] Close button should dispose editable
[√] add index:
[√] reload ui after add index to show it
[√] delete index
[√] geberit ar24 esrs had unsaved changes (asterisk) after load -> reset stores
[√] initiate new index with valid data
[√] Ask JD how to enable other reports? -> Waiting for anwer
[√] Delete info from options drawer

Relogin:
[√] Look why UserAvatar showed unexpected for Albert suddenly
[√] UserAvatar should not show unexpected but should provide relogin modal
[√] Make relogin for sso and dologin to solve Albert issue. -> Done whole relogin including wb because it doesn't hurt and was easy to reuse the whole Login component

Reinstate rendering:
[√] FED/CMS: Geberit gri Accordeon geht bei block nicht? 
[√] FED/CMS: Checken ob headaer fehlt im CMS —> Ticket erstellt

Stylesheet:
- [x] If not find it: Ask if there is a special node or if i juse use a lynx node https://nexxar.atlassian.net/browse/NXRCMS-4667 No, the other tickets suggests to create a default or common node for this. 
[√] Look for a special/general lynx config node in the gql api. —> No, there is not. And also no mutation to change it. Only report > lynx > original node is suspicious, but it's null and mutations for it are missing
[√] Delete Stylesheet node. Will be regular node with name stylesheet
[√] Dont display styleseet card initially.
[√] make button to add a stylesheet when no stylesheet exists
[√] Button creates node with name styleheet
[√] Add stylesheet should initiate stylesheet with template data
[√] Paste all configs new on staging since i changed the config data structure (types, data) —> did one
[√] Verify that saving saves with the correct type "Index" / "Stylesheet" -> did now without type but with new "data" field instead of "indexNodeData"
[√] Test loading stylesheets.
[√] To Save at stylesheet at send via WB API
[√] Test update to CMS
[√] Ev. desktop kicken und nur mobile verwenden, mobile ist default.
[√] Style: Center StylesheetMain
[√] Style: Filename should be at left of open all button.
[√] StylesheetMain soll bis am boden gehen
[√] Filenam xl again
[√] Fix update stylesheet filename on production. Currently reactivity does not work in input field
[√] We need "lynx-acc-trigger" with same rules as healdines. This has to be used instead of .headline.headline--1 and co. whenever some headline becomes an accordeon
[√] And also the lynx-acc-trigger Input fields UI on the left
[√] Multiple stylesheets ToggleButton should become navigatable
[√] Finnish active/inactive css rules
[√] Nice to have: CSS Syntax highlight or css editor.
[√] .lynx-table__cell duplicates text settings (font size, line-height und co.) of .lynx p.: Only use them at .lynx p 
[√] Add special css from the bottom also to ui. F.E. to inbetween-columns or this last hide thing to table_cell ect... Test with EnergieAG
[√] Add .lynx with padding bottom to UI General
[√] Test set gap to 0 to disable inbetween cols -> Does not work
[√] Make inbetween  border bottom editable to visually disable inbetween columns
[√] Make a button at raw css editor to show the compiled css.
[√] Compile: Revmoe block comments, inline comments and empty selectors.
[√] Add compiler to save
[√] No view in cms button at stylesheet

Todos:
[√] Serialize issue: Single language darf nicht gleiche sprache in output anzeigen. Zeigt im moment immer zb 'en', somit wird es in 'de' nie im cms angezeigt.
[√] serialize Breadcrumbs
[√] Test new View-in-CMS target set process
[√] Verify Re-login on staging

Akkordeon:
- [x] Also ask Tina if only one accordion per index is possible -> I am prettiy sure this is the case
- [x] Ask tina what happens if on a page is a lynx accordeon and a accordeon outside of lynx. in cms editor is tabacc_selector: .lynx .lynx-acc-trigger, but does a accordeon ouside of lynx need another selector and are two different selectors possible? -> Well this must work since i think it was done at merck
[√] Akkordeon swallows next parent caption -> Ticket geschickt: https://app.productive.io/17342-nexxar-gmbh/tasks/14984488 -> no-tabccordion vergeben

Code:
- [x] lynx rendered html und klassen statt FED (Mehr kontrolle)
- [x] Show stored output and create output (what output will look at next save)
- [x] Console logs entfernen für einen hauch mehr tempo
- [x] Performance: content rendered on mount 2x (bei akkordeon schließen und wieder öffenen renderd es beim öffenen nicht mehr so oft)
- [x] flat data structure for better typesafety
[√] output page must be directly after reportid slug
[√] Make field use also <InsertMenu /> (like all the other components) instead of showing it's own Dialogs.
[√] Performance: Render all dialogs conditinally, like text dialog, it only loads it's children when isOpen is true. Jeder dialog created schon sein item. initial performance
[√] Backlinking runs every time. Put it inside a function
[√] Mark config stuff as obligate
[√] Refactore from features/ to pages/. Also maybe flatten folders do reduce ../../shared.
[√] Make types less optional in Config
[√] change store slices to seperate stores and remove history/config and config/clipboard interactivity. Use hook instead for history.
[√] Pages data should go from <reportId>/<indexNodeId>/data/pages to <reportId>/data/pages

Optional:
- [x] search and replace > list unique texts
- [x] unique service links list
- [x] Colspan headers made visible, also in content view
- [x] make preview, maybe even style directly in preview like in kitaco, but still append open css. error handling when css comment is not found
- [x] schauen ob new line mit \n drin ist und wenn schon mit <br/> ersetzen
- [x] bereits fix fertig zusammengebaute links (custom text und anchors) soll es vorschlagen in link dialog. soll rechts ein fenster sein und einfach gleich mitfiltern haha. wäre bei omv zb eine hilfe am schluss gesewesen ein bisschen.
- [x] implement set "utility classes" via content sub-sub-menu, predefine classes in lynx.css, and in output.ts, merge to custom classes.
- [x] colspan auch auf button oben legen, es kann dann einfach die zahl eingestellt werden. muss nicht multi cell sein.
- [x] Accordeon with base ui
- [x] in text edit: toggle for html syntax
- [x] Dashboard: group recently used reports by client
- [x] content view drag and scroll up
- [x] In content view auch hintergrundfarben machen wie in structure view?
- [x] External link edit should also be commitable with enter key
- [x] Categories at stylesheet to make it visually easier to read
- [x] make view in cms target removeable
- [x] Gemischt Text und link multi selecten
- [x] Dashboard: structure last used by dates. today, this week, this month, older
- [x] Base UI Toast
- [x] Base UI Tooltips
- [x] Stylesheet: Show warning when not logged in into workbench, tell user to log out an in again, or even better let him log in to workbench in place.
- [x] Stylesheet: Add alignment bottom and top everywhere it makes sence
- [x] Stylesheet: When everything is open, you cant scroll in the css editor because it is higher than the screen and scrolling is to short then. PUT css editor in a drawer on the left. inside the draewr should then be a accordeon for the profiles that are all open by default.
- [x] Styling: hadlines text transform uppercase oder none als select anbieten. Beispiel voest. Da ist von FED uppercase und wir wolle ndas nicht.
- [x] Structure view: bei drop as children soll sich akkordeon öffenen
- [x] Report selection categories (Annual reports, sustainability reports), or sort by year. (try dtag)
- [x] Dann auch index klass nach links oben in die ecke geben.
- [x] Paste content between indices
- [x] Everything keyboard navigatiable 
- [x] Icons and links do break to a new line
[√] Stylesheet button nach links geben und "To stylesheet" nennen.
[√] report overview cards have less height then index overview cards. (report card height is better)
[√] remove x at index overview cards.
[√] what is CalculatedLabels
[√] disable adding special items like table/icon/list inline beside other text. The special items will win the render and the inline siblings will be removed
[√] copy line, select other line, paste below
[√] The empty field shows a grey box on hover, it should add items
[√] output page must be directly after reportid slug
[√] Make field use also <InsertMenu /> (like all the other components) instead of showing it's own Dialogs.
[√] Performance: Render all dialogs conditinally, like text dialog, it only loads it's children when isOpen is true. Jeder dialog created schon sein item. initial performance
[√] Backlinking runs every time. Put it inside a function
[√] Nice to have: internes linkfeld soll auch interner link als überschrift haben. text dialog auch text aber nur im großen fenster.
[√] Style: Strucure headline skeleton muss dunkler aber gleich dick
[√] Ev class indications immer grau machen dass man sieht das man klicken kann.
[√] Tooltips auf die class dings draufgeben
[√] Styling: eliminate the input fields that should not be used. For example text color should not be available on both header and header cell. Only header cell is enough.
[√] links ancher ersetzen tool -> Integrated in unique link list
[√] Nive to have: ev. die grünen class Kästchen noch etwas grö´ßer machen

Bugs:
[√] headline classes are not updateable
[√] Edit text > drag highlight with mouse > hit delete key to delete the selected text > text item will be deleted completely. Solve or disable delete items with delete key.
[√] Insert text in line, or inbewteen lines > fine > Do it again in the same line > Popup flashes > Drag and drop the just added item > Popup automatically opens: Unsolvable!: Option 2: Initial text item with normal modal (like other items) and get rid of justAddedTextId (it is very hard to solve)
[√] In a line, click in the right area, below the delete button > Line deletes.
[√] Drop a line on a item: Item suddenly looks like a line as is not fully deletable anymore. Artefacts remain.
[√] copy paste somehere throws: hook.js:608 Encountered two children with the same key.
[√] Edge case: Internal links unique list is not really unique: Add post "test" at one link, and at another place add "test" it to the main link text. Only one is found. Reason: It checks equality by full title.
[√] unexpected at restructureAnchors
[√] Lindt SR 23 > GRI > In row 2-3 click on link "Basis of preperation" > error >	Reason is originalTitle i think, this is why it only failes at lind, because this was done before original titles existed (maybe also energie ag)
[√] Lindt SR 23 > open revalidate links Dialog > error Reason: this hopefully resolves with the above
[√] Lindt SR 23 > Copy data to localhost > save > error	Reason: this hopefully resolves with the above
[√] https://lynx-dev.nexxar.com/#/Lindt%20&%20Spr%C3%BCngli/d85c6041-8917-4ed0-96cd-c57dfb045b48/output/ > Uncaught Error: Error at serializing internal link: missing structureId
[√] https://lynx-dev.nexxar.com/#/Geberit/46c147c4-863a-46b6-88dc-8641601b45ca
[√] - "Uncaught TypeError: Cannot read properties of null (reading 'type') at pasteActions.ts:97:20" happens because clipboard is empty, but seletion not
[√] Pasten in unique list dialogs pastet auch in content:
	[√] can clipboard hook be selector?
	[√] Same with selection store
	[√] abort copy also aborts selection
	[√] Color popover also needs abort stuff
	[√] Add to unique dialogs
	
Upload:
// C:\Users\StefanR\Desktop\Lynx\feature-test-imports
[√] Support 18px only headlines
[√] Support missing levels
[√] Support hierachy mix

Download:
[√] Check

Prepare backlinking:
[√] Check normal backlinking
- [x] Check multi backlinking from last season  (basf esrs?) --> Does not exist. BASF ESRS has ESRS backlinking insteaf of GRI backlinking but that is handled with cms editors option
[√] Find indexes that use split and backlinking. -> Does not exist
- [x] Backlinking is broken, name property is empty -> No, everything is fine, backlinking just needs a first column to get it's description from
[√] Find a solution to apply backlinking across blocks. -> Was never needed at split indexes but still
[√] Make last test with manually modified backlink to fix redirect issue
	[√] linkt falsch zurück --> Muss kombiniert werden im JSON damit jeder Eintrag nur einmal ist
[√] Warum finde ich "Lagebericht der Konzernleitung" nicht in den Pages? --> Copied wrong report

Check Split:
[√] Find indexes that uses split. --> voest
[√] Rebuild as blocks -> Voest implementation was veeery splitted. Will be same with blocks. One page combines ~10 blocks, and individual blocks also appear on other places.

Prepare one language only:
[√] Find indexes that use one language only. (Sandvik, Lenzing, ...)
[√] Rebuild as block
[√] Find lenzing id translation solution

General:
[√] Index class not working --> Write ticket to Tina --> Ticket is written
[√] Annotation works?
[√] Tina fragen ob das render template jetzt überall dabei ist
[√] Does spans to bottom still work? Check border styling in CMS -> With new css it works. The functionallity is intact.
[√] Klammer als Sonderzeichen ausnehmen bei id vergabe

Inroduce footnotes:
[√] Test at geberit staging
[√] Check footnote stylings in all reports to get a picture -> looked at BASF at least
[√] Type footnote: Attributes: text, reference.
[√] Make addable
[√] Render
[√] Serialize: Put footnote and optinal siblings into a wrapper object.
[√] Fix pipeline
[√] Add ui to edit customClass.
[√] Add custom footnote class action
[√] Add custom class in serialization.
[√] Merge to staging.
[√] Save an example footnote to the CMS at geberit.
[√] Check if rendering is broken. If so keep in mind and do not deploy unless footnotes are rendered -> Is ont broken
[√] Write Ticket for Tina ./examples/footnote.notes.
[√] Select item, edit footnote, press delete, item is deleted
[√] Check backlinking, download and merged cells again.
[√] Fußnoten styling adden when ticket is done
[√] Test footnote styling
[√] Change UI to:
	[√] Space before footnotes (footnotes padding top)
		[√] CSS
		[√] UI
	[√] Space between footnotes (tr td: padding bottom)
		[√] CSS
		[√] UI
	[√] Space bewtween reference and text
		[√] CSS
		[√] UI
	[√] Footnote font styling
		[√] CSS
		[√] UI
[√] Last footnote row should get fixed no space below -> fixed
[√] Test again -> Works well
- [x] Hochstellung mit css -> Nein mit sup, derweil händisch


Prepare stylesheets:
[√] JD bug fragen
- [x] Paste data to nodes.
- [x] Embed block on hippo-staging
- [x] Reset stylesheet and rebuild style
- [x] Save new stylesheet as file in case staging gets reset

Dashboard:
// ignore index level for now.
- [x] "Recently used": Categorize reports per client display client only once.
- [x] Last click report should cuase the client box to be first
- [x] "Continue with" should actually use the latest clicked index
- [x] "Continue with" whould have all clickable slugs.
// introduce index level
- [x] Add last used index to "Continue with"
- [x] if possible add indexes also to "Recently used"
// simplified

Production bugs:
[√] search an replace fixen
[√] auch auf staging
[√] Trenner automatisch einfügen
[√] Auch auf staging

Important:
[√] initial load dauert zu lange für index. seit neuer option? oder seit localstorage? --> Passt eh noch, war vl. wegen Energiesparmodus, dass es da browser kapazität beschränkt
[√] Überprüfen ob eh nicht alte styles droben sind. Bei Inpex war es ja auch schon
[√] Dann umstellen dass staging nicht mehr auf cms speichert

Versioning:
[√] JD fragen warum versions leer sind. examples/versions-query.notes
[√] fix retrieve versions
[√] fix restore version

Dashboard simplified:
[√] Move localstorage tracking trigger from report to index. Target structure: examples/localstorage.notes
[√] Change UI only show "Recently opened", but for index level: Client > Report > Index. Remove continue with section.
[√] Make every slug clickable
[√] bei klick auf index kommt er korrekt in local storage. beim zweiten klick drauf (in dashboard) fehlen dann client und report name
[√] Favorites component umbenennen

Next:
[√] main auf stand production bringen, dann auf main weiterarbeiten

Improve UX:
[√] Der project selector ist vertical nicht ganz aligned (drop down buttons sind zu hoch oben) -> Check if stylesheet select still works
[√] Leere dashboard einträge nicht anzeigen -> local storage gelöscht, jetzt gehts wieder. Weiß nicht warum da schon was drin war für lynx.nexxar.com

Bugs:
- [x] Jo hatte unexpected beim user. Warum war das? -> Zu lange nicht neu geladen mal auf jeden fall
- [x] gri hat nicht geladen bei geberit beim herzeigen. (Mir aufgefallen) --> Sagen wir es ist wegen langsamer browser memory wegen screen sharing

Communicate:
[√] Jo sagen wann er bei Fresenius AR testen kann

Branch:
- "full-circle-xlsx"

Translation workflow:
- Mein ansatz reicht nur einzelinhalte in zellen ins excel auszugeben, paragraphs ist nicht notwendig. Jo hatte aber kaum übersetzungen.

Export:
- [x] No need for plain text anymore, it can be plain text all the time
- [x] Issue: Items within line. Words within paragraph. Color code? or some syntax? -> Makes no sence since editing this that granular in excel is more pain then in lynx itsel
- [x] Optional: Implement drag and drop file into lynx
[√] Store whole json in cell note.
[√] Issue: row classes: Store in additional cell -> Store just row classes; Do this in first cell to avoid used cell range complexity.
[√] Optional: Download should not merge cells
[√] When exported as plain, don't add comments to not make the impression that reimport would work
[√] Store header data also in note for col width and everything
[√] flatten must save level to footnote in the first place

Import:
[√] Optional: Empty headlines should not add default text. Works on sublevels, but not on root level.
[√] At upload merge title in cell json.
[√] Issue: index data: Paste just rows and labels, the index node always exist, both on reupload and initial upload. This way there is not title mismatch issue. Better then storing index data in excel. And settings like breadcrumb settings stay at reimport and are not set anyway at initial import. -> Already is that way
[√] Read in header data at recreate from json and merge with title
[√] at import overwrite level in data with the excel level to support changing hierarchy in excel
[√] When last cell is empty, no field is created (only when field has f.e. border). Used at HHLA, Lenzing GRI, 

Export Footnotes:
[√] Add footnotes
[√] Implement that footnote does not need a reference

Import Footnotes:
[√] Import: Footnote level should no be overwritten by excel level, because this moves footnotes always directly under the last indicator instead of keeping it at the very bottom
[√] Recreate footnotes
[√] Create footnotes

Test:
- [x] No row type is determined by effectefly last cell (iterates every cell and every cell pushes type to row) -> Change this so that first cell is what counts
- [x] Change that not the last cell but the first cell font size is important at footnote -> Not important, nobody would only mark the first cell, at least the whole footnote content, and thats enough
[√] Test Muss die ganze Zeile die font size haben? Adabt in confluence docu? -> Only footnotes. Headline only looks at first cell. Indicator is defined negatively (no headline, no footnote), so the font size does not matter. And footnote is the only thing that is effected: The last cell counts.
[√] Change in docu that not whole cell hast to have font-size and also that not the whole document has to be set to 12px
[√] Test Footnote without reference or text -> Does not work
[√] Does header need to be font size 11? -> No, edited in confluence
[√] Test isPlainText
[√] Test an empty row to a structural, we had this case a few times
[√] Test if classes are preserved.
[√] Test if accordeons are preserved at headlines.
[√] Test real live uploads from last season

Final:
[√] In hook loading indication and error modal wieder aktivieren
[√] Delete unused files
[√] Fix pipeline -> build ran through, audit not, but fix audit on main after merging
[√] merge to main and production and solve conflicts

Nice to have:
[√] Initial upload should make col width to total 100%

Dont't repeat header:
[√] Pre group indicators. Search for `TODO: pre-group-indicators` in the project. Use the logic from serializeRows() # siblings indicators header legend -> did not need the logic of serializeRows.

Test:
[√] adidas
[√] hhla

Upload 4th level is ignored:
[√] Status
- Location: Everywhere.
- Reproduce: Upload "C:\Users\StefanR\Documents\Lynx\files\upload\feature-test-imports\GRI_download_2024.xlsx" somewhere.
- Issue: 4th level is not nested

[√] Tina ins ticket schreiben wo überall lynx regeln im main.css drin sind: https://app.productive.io/17342-nexxar-gmbh/task/15281002: HHLA
	// Where it is already correct (or never in main.css):
	[√] Adidas AR25
	[√] BASF AR25
	[√] Beiersdorf AR25
	[√] BLG AR25
	[√] Chevron Phillips AR25
	// [ ] DTAG CR25 -> ERst später online
	[√] DSM-Firmenich AR25
	[√] Energie AG AR25 (noch ohne Lynx Block umgesetzt → nächstes Jahr)
	[√] Geberit AR25
	- [x] HHLA AR25
	- [x] Jeronimo Martins AR25
	- [x] Lenzing AR25
	[√] Merck AR25
	[√] OMV AR25
	- [x] Sandvik AR25
	// [ ] SIG AR25 -> lynx template not yet implemented but i dont think so
	- [x] Voest AR25
	[√] VW AR25
- [x] Ticket links vervollständigen: Dummies anlegen, oder gleich richtigen index reinpasten: Ist überall wo es schon geht derweil. Auf Tina warten für SIG bzw. einfach zuwarten für dtag.

Todo:
[√] headline only look in first cell for font size
- [x] footnote only in first field errors wich is ok but make nicer error message > Can't reproduce
[√] Test xlsx again
[√] deploy production

[√] Delete Dummy indexes where possible
	[√] adidas 
	[√] basf
	[√] beiersdorf
	[√] ev Sandvik GRI is discontinued, now other Indices -> A few pixels off but gaps area weird anyway, it's good enough
	[√] hhla

[√] Quick test one index update on production

Reported:
[√] Albert got unexpected at useravatar and save was not possible anymore. Fix or make relogin possible. See todos. -> Done on staging
[√] When click on picker selection it does not warn Make warning like as user clicks on picker title

Bugs:
[√] Delete columns: Last column is deleted always
[√] Each child in a list should have a unique "key" prop.
[√] Empty texts are not reachable: Location: Content and vtructure view. Text item. Other itmes also? Delete text from a textitem. Empty textitem is not clickable in headline, and almost not in indicator; Example: User gets stuck, cant grab the item anymore

Other:
- [x] Nice to have: Stylesheet: Table header cell aus Cell rausnehmen und eigenen Punkt machen mit der Überschrift Table header cell. Und den Punkt Cell umbenennen zu Body Cell
[√] Upload xlsx should ignore missing levels (low prio)


Improve locks:
!Branch: auto-close → main → production
- [x] Don't mess up saved/unsaved handling > No interference
[√] Remove Unlock button
[√] Unlock on leave -> Maybe where indexNode store is reset
[√] Unlock on close browser → can't unlock can only warn when user is on index node layout.
[√] back button → Search for DISPOSE EDITABLE NOW and implement there, this is the right place.
[√] test on dev
[√] deploy to prod

Break lock adcanced:
[√] Benachrichtigen wenn jemand anders den lock bricht. Wenn man es offen hat sieht man es sonst nicht und arbeitet einfach weiter. Auch im offenen index alle paar sekunden verfügbarkeit abfragen. wenn wer anderer lock bricht, dann soll es einen raushauen zurück zur Übersicht.

Remove content filter headline classes only at pdf stylesheet:
[√] Consider duplicate to produce a pdf stylesheet

Quality:
[√] Move the flatten() function to @/utils since serialize uses it ans also backlinking
[√] In backlinkings getRowsPerTargets() function, filter the flattendRows for type Indicator (immediatelly after flattenRows(rows)) and then delete all the following type questions.

Stylesheet:
Headlines:
- [x] h2 statt h2.headline-2 und co weil im pdf die klassen anders zugeteilt werden

Bugs:
[√] - backlinking bug: https://hippo.nexxar.com/clients/dsmfirmenich/iar25/en/sustainability-statements/other-information/esrs-content-index#lynx-esrs-iro-1
	[√] backlinking ist nicht richtig von den zielen her
	[√] und ids sind nicht klein. GOV-3

Nice to have:
[√] bring back the categorized view for recently used. If done trim the breadcrumb view to the first entry and name it "continue with" to get the complex version of the dashboard.
[√] Will "continue with stylesheet" work in dashoard page
- [x] Order indices alphabetically on report page
- [x] Text drückt die Zelle höher als links. Try link und text in one line
[√] Sometimes when lynx is open and session expires, it just get stuck on the next action and loads forever. It should check if the session is still on.
[√] Whether shadow at every white card in menu and options drawer or not → not
- [x] View in CMS: Re-select page should not trigger the dialog. display the dialog only at first page select.

[√] Delete index actually should be in the menu drawer instead of the options drawer since it an data action, not a setting

UX:
[√] Die class eckerl noch ein bisschen größer machen
[√] test extensivly, also saving and everything.