
- Deploy script von Hedwig für alle s-share programme machen

- Implement AI in programs where interpretation is needed. AI is Under the hood, no human in the loop design.

- excel: Harte enter ausgeben lassen in tabfile

- Sachen im cms suchen verbessern, wie tabelle usw, wie tab name caption oder content suchen können wäre schön

- Workbench mock api in typescript for kitaco and live stats development. Oder proxies wie bei sso-portal?

## Asset-Management

- Live editor
- wunsch nach assets management von FE
- einige dinge gingen mit datenbank besser, konflikte wenn jemand auf transfer arbeitet oder mit cms editor editiert

## Tool zum Tabellen suchen

replacements app wo man alles mögliche einstellen kann. und es highlighted im dokument immer alles schön.
vl auch dass man das dokument direkt bearbeiten kann an den entsprechenden stellen.

## Befüllungscheck (Pecker) 🐦

(saturnia access, file uploaden)
zunächst mal im lynx repo probieren. html file soll einfach hochgeladen werden.
Can be extended to a full blown the-ones-that-got-away-check. Includes horst and TE checking for checks client edits in the cms. Improoves text quality long after we gave it out of our hands. Improoves text qualty right before got live.

## DMS Text Cleaner

consume CMS API
Extend to full Textexport app which has file import and file export.

## Search for tables in cms

look up tables in cms

## Antilope — Add next table edits & live operations

- JSON to Excel Converter and Excel to JSON Parser # prerequisite
- Storage # prerequisite
- edit content # only office does this already, half feature
- WYSIWYG styling for kitab-config.json, also for PDF styles # expensive feature
- excel import/export
- table aufziehen (Mehrwert), reads styles from kitaco
- table populating in app (hard)
- saving exports tab file and starts current convert tables and upload tables OR write own table conversion tool



## General Txt Repl

// Duplicates teammate tasks
upload, change, download.
it could read the master excel as input and then make dropdown but automatically suggest the repls of the specific client. yes.
Fine grained control, history, everything, sensitivity and density of nbsps. have list of stuff. lots of lists, from everywhere. all the lists should be external, in the file system, but loaded in in the app and edited in the app in later versions.
the app just fucking reads this stuff and gives you actions on the text. no business logic should be in the app. all the bl should be in the lists. yes.
just paste text in, edit it, and copy back out. simple.
or maybe make imports. import word possible? or maybe the exported html?
what about horst, well he can run after the html or after the text is pasted back.
names: typewriter, char

## Assets editor

find tables in input
init or update assets automatically
task styling finden


## Sparetime

Origami: (from notes to tickets, wrap up, make objective from notes sheet, from note paper to clear picture, organizer gamifyd)
list notes and tasks like in confluence
add prio, lables and comments
view to group by prio and lables
mark text or create task from it
mark groups and create tasks with automatic subtasks from it

## Office.js

- 

## Offline tables

- All tables in einer wurscht anzeigen anstatt mit next durchklicken.

## Ticket app

Nav: Ticets, My actions
History page nav: All actions in categorized per ticket (collapsible)

## html div app
für textexport tests

## Older

- Tool um tabs im cms zu finden. Sowol kurzname als auch langname. Kuzname in .table.name-short-name und Langname in caption. CMS html durchsuchen wie horst? structur durchsuchen? wie horst besser. code holena
- Offline tabs: switch to english button
- ask for workbench labels and api to get them. can be used instead of documentation.
- splitten außerhalb von excel machen damit excel und strg c strg v nicht blockiert ist
- jo idee: geberid mit nxr id ersetzen und gleich fix tabellenname eintragen. damit man jederzeit drauf verlinken kann.
- _materials sprachunabhängig (jo)
- css überall aufräumen? .table verwenden
- silbentrennung in officejs einbauen mit AI
- silbentrennung electon ai app
-	Eigenes disclosure mgmt machen, dass nicht auf word beruht (aber words ausspucken kann), und Smartnotes, workiva und das ganze Zeug ersetzt.
	- Source of truth in jsons, nicht Word,
	- kann aber Word files genereieren (Die Kunde dann auf diese offiziellen Plattformen hochalden kann)
	- und Word files importieren (Kundeninput)
	- Kann direkt ins CMS importieren
	- Ersetzt Smartnotes, Workiva, usw..
	- Ersetzt word importer"
	- Multilang (nicht nur de und en)
	- Kurzfristig: Wir importieren Word und setzen damit um
	- Langristig: Kunde arbeitet von anfang an im Tool und exportier sich word nur am Schluss wenn ers braucht.
	- "discl. mgmt -> Word" bzw. "discl. mgmt -> CMS"
	- Neuer Bericht startet mit VJ-Daten vom CMS. Dann wird im discl. mgmt direkt gearbeitet. Jederzeit dazwischen wird Stand ins CMS geladen. Und optional jederzeit ein Word daruas gezogen.
	- Probleme: Konflikt mit Saturnia (oder CMS-Editor).

## Utitlity App

- Auth: Workbench to access workbench
- File zugriff: Workbench enpoints: Bei bedarf nach mehr endpoints fragen.
- Database: Same repo? extra server?

## Table app

### Core concept
- Soure of truth is webbased JSON (stored in database, editable via web application): Allows external and internal use.
- Table scope instead of tabfile scope. Different tables can be edited by different people at the same time.
- Fully two way convertable to XLSX to support doing everythin in Excel that will always work best in excel. table 
- Table knows it's place in the CMS and vice verca. Direct linking.
- Prep will reduce significantly.
- Styling will be more global (not every border per hand). Instead the elements know what they are, header, current year and co. Will need manual work to assign thogh.

### Talk
- Talk with mario about workiva api (horst). Then try it out.
- Talk with jd about how tables are in workiva and if they can keep them as placeholders

### Current
Workiva > Word > Textexport > Excel Tabellen > Kitaco > Kitab > CMS

### Consider1
Workiva > API > Content > Tabellen extrahieren > Tabellen taggen > Style config updaten > HTML generieren > In upload ordner legen* > update tables triggern**
// Workiva---   Web app----------------------------------------------------------------------------------   WB------------------------------------------------

### Consnider2
Workiva > API > Content > Tabellen extrahieren > Tabellen taggen > Style config updaten > JSON generiergen > Neue Blöcke

### Retrieve tables
- Consume Workiva API: Own API // Node.js backend (or Next.js) with express or fastify. Expose tables
- Extract tables from content: Same API
- Parse tables to JSON: Same API
- Tag tables: Seperate UI or same if Next.js // (what is header, what is footnote) (very hard and extensive) (restructure JSON): Client Web app or same backend if it is Next.js
- Generate Stylesheet from config: Same UI // Select/create Config (excel styles + kitaco): Get config from kitaco? Kitaco would need to become a API (full stack or node.js backend). Or get kitab-config.json but two issues: no file access possible (runs outside vpn, same as cms) and sharing sharing it with kitab.
- Save: UI sends final JSON to backend, backend puts it in database and also exposes an enpoint for the ui to edit it again.
- Send to cms: UI 

### MEARN
// or acitally Node.js + Fastify/Express + React + SQL lite / Postgres
- UI triggers Node endpoint
- Node Endpoint gets content from workive, extracts tables and parses them to JSON and expose them
- UI tags tables and applies styling. Then save. THIS IS THE HEART OF THE PROCESS, SINCE THIS MAKES OLD TABILES AND EXCEL REDUNDANT
- Node saves wip json to database
- UI triggers update to CMS
- Node puts them via whippo/new block or node might run behind vpn and writes html tables and puts them in upload folder and triggers upload.

### Excel approach
- UI triggers Node endpoint
- Node Endpoint gets content from workive, extracts tables and parses them to JSON AND EXCEL
- Excel can be editet. ISSUE: STYLING HAS TO BE DONE, OLD TABILE TO BE USED -> NO PROGRESS
- Styles are done in kitaco
- UI triggers updload
conlusion: NOTHING GAINED Excel must be spared out in order to achive progress. Why? Because Excel requiers styling the tables in excel and therefore we need old tabifile and we gained nothing.
Except: Must the styling really be in excel? or can we use plain excel and styling comes in app. But still, we need the UI to style, and then why use excel at all. The data is not the issue, thats already there.

### Onlyoffice Approach
Does not help much since the styling needs to be done somewhere. And the place where its done can as well carry the data. The data is not the issue. The styling is. Data is not the issue because befilling only ever existed because we want to reuse already styled tabfiles. Data actually just needs to be as is from workiva. If data retrievel is a problem, therer is no new approach.
conclusion: Nothing Gained.

### Soucre of truth
- Cut from workiva and from there on app is the SOT: Process does not need to be repeated but cut is not optimal.
- Workiva stays source SOT: Process must be repeatable. Issue with tagging tables.
	Tagging must be a tralation/replacement map that can be applied anytime. But very hard to make and very error prone if people change somehting in workiva.

### Issues
- Position/Zuweisen/Struktur: DMS importer (BED) needs to already apply placeholders. We then need to use the same names. We need to retrieve the placeholders and match our tables to them.

### Research
Was ist ein Monorepo? Monorepo vs. lauter einzelne tools.
Ich kann mir lauter einzelne tools besser vorstellen aber warum ist Monorepo so populär?
What does runs outside of vpn mean in network terms?

*WB Tabellen in upload ordner legen? Filezugriff problem
** update 

### Personal notes
I want to make the Node.js backend. Or even next.js
The UI is even less important for me in this case. But still i wanna do it, yes.

### Older

tabfile
individualize table settings
tabstyle css
snippets
kitabconfig json
alles einlesen
edit view rendern
zu html rendern
alles schreiben
### Issues

Zahlenformat
Css: string

```json
Data: {
	Table {
		TableRow {
			TableCell {
				TableCellContent: LanguageObject
				TableCellStyling: {
					TableCellBorder: BorderObject
					TableCellBackgroundColor: string
				}
			}
		}
	}
}
LanguageObject: {
	language: string
	text: string
}
BorderObject: {
	top: {
		color: string
		width: string
	}
	right...
}
```




---------------------------
## Names


Matrix
Panel
Cells
CellStack
Cluster
Sheet

CellStack
CellBundle
FlexCell

FlexMatrix
FlowMatrix

FlexTable
FlowTable
ModTable

FlowSheet
FlexSheet

Weave

sheets
TableStore
koala
TableDB
SpreadStore
TableShare
TableHatch
TabHatch
spreads
sheets
Lovely
Finch - Financial cell hub - files in nexxars central hub
Koala - key online access layout arrangements
hatch
nest
store
finchStore
TableStore
CellDB
SheetDB
TabHub
TabDB
TabStore
CellStore
SpreadDB
CellHub
Cellular
CellularDB
Dole 
ssot
amphibia
cellpole
cellpool
cell
tad - table data base
celltank
tabletank
Finch - flexible integrating cell hub - flex incorporate hub - format integrate create hub
Vault
finta
cellNest
tableNest
spr
cellHatch
TadDB 
AmphiDB 
CellVortex 




stilt - storage i live tables
goose - optimized online spreadsheet editing - g? open online spreadsheet editing - goose olinine 
guided globally granular gesture gather generic governance
open/optimized
guided open online spreadsheet editing
goosey spreadsheet editing
guided optimized online spreadsheet editing !!

Goose: Generate online statistic evaluations
Bee: Benchmark Evaluations

spreasheet editing - g oriented online spreadsheet editing - 
antelope -  teleport online persinsance - ant... eleborated per - .. live online persistence

anelope - an eleborated onlnne p editing


antizipated eleborate operation edits
antizipated eloquent performance
anteligence lopeless
ANTicipated ELOquent Performance Optimization, LOPE-less and Effortless
ANTicipated ELOquent PEformance

Antizipate Table 
ANtizipate TELe 
ANtizipated Table Editing Live OPErateions

Application Nexxar Table Ediging Live Optimized Process Experience
Live Optimized PErformance
AN Table Editing Lope/less

----

🦌 ANTELOPE - Add next table edits live operations - Add next tab element ops - apply new tab edit live ops - Adaptive Networked Table experience and Live Operations - Adjustale Newtorkecd Table Editing Live OPErations - A N Table eleborate 
GOOSE - Guided Optimized Online Spreadhseet Editing
ANTS - Adjustable Networked Table Storage - A Network Table System - Adaptive Networked Tab Sheets
ANTS (statt Kitaco) - Add next table styles -  ANTicipated Styles - Adjustable networked tab styles - adjustable & new tab styles - adjustable nexxar tab styles - anticipated styles

Accumulative Nonlinear Table Editing and Live Operations

Antizipated Table Edits and Live Operations
Anticipative Table-Editing and Live-Operations
All Network Table Edition L
Guided Open online spreadsheet editing
Goose spreadsheet editing
Table editing for local and online process 
table storeage
local online conveersion
apply next table edits local online process environment
table environment 


cell hatch

SW🦢N

 Goose — Get Overall Online Statistics Easily
🐐 Goat — Get Online Analytics Today
🦌 Antelope — Add Next Table Edit live operation
🐠 CellKoi
🐟 TabTuna





