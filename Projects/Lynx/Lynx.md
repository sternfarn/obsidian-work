# Today
- [x] H1 feature fertig machen
# General
- [x] anderer chat zu header text edit issue hat problem noch nicht gelöst.
- [x] Energie AG index migrieren
- [ ] #jd fragen, wenn er wieder da ist. OMV issue weiterleiten.  [This](https://hippo.nexxar.com/clients/omv/ar25/en/directors-report-sustainability-statement/esrs-2-general-information/statement-on-due-diligence) and [this](https://hippo.nexxar.com/clients/omv/ar25/en/directors-report-sustainability-statement/esrs-2-general-information/statement-on-due-diligence/risk-management) page are missing in [Saturnia](https://saturnia.nexxar.com/main/clients/1f4d521b-f6c5-48d0-be2f-9a4e1abb68e2/reports/6163546b-1e9c-4c91-aae3-f215293c0bb3/versions) and [Lynx](https://lynx.nexxar.com/#/OMV/6163546b-1e9c-4c91-aae3-f215293c0bb3/c9c518d1-5043-4a97-8c1b-6688e9d1ef12/content)
# Shareholders
## MD
- [ ] Tickets, Workshop für PM's (less relevant since PM shortage)
## Jo
- [ ] Tickets (anker, update, split)
- [ ] Geberit automatisieren um Jo für alle neuerungen zu gewinnen
## MN
- [ ] deep link von nexxar start her auflösen (report name zu report id)
## SR
- [[#Table view]]
- [[#Table paradigm must-haves]]
## PM
- [ ] [[#Table view]]?
## COM/PD
- [ ] [[AI]]
# Multi header
- [x] FTL: styling der header cell ist zentiert und muss angepasst werden, ist wegen th

# Topic exists as ticket
## Anchor links
### General
- [x] visit bei anker links funkionierend machen
- [ ] "Original title" in edit dialog muss anders heißen
- [ ] plan file other stages fertig machen und belgeitende pläne (breadcrumbs)
- [ ] JD ev. query schicken
### Link picker
- [ ] im link picker visit symbol bei pages auch rechts
- [ ] headlines und setien besser unterscheiden können
- [ ] headlines hiereachie checken mit einrückungen usw. (wissen wir die info?)
- [ ] focus filter field on open
- [ ] keyboard nav
## Split
BlueprintNode/DerivedNode: Blueprint node creates drived (splitted) read only nodes on save. Derived nodes are shown disabled and indented under the blueprint node
# Workiva
/20k/new table process
~~Kein anlegen der nodes.~~ → On click anlegen anhand der assets oder des imports
Kein Textexport, Excel upload-file creation und import. node für node
[Ticket](https://nexxar.atlassian.net/browse/NXRCMS-5099)
1. **Tabellen als index markiert**, . In workiva runde besprechen...
	- Tabelleneigenschaft oder Mapping.
	- Schöne Namen oder interne ids.
	- Assets müssten gemachted werden, damit spätere updates funcioniert im Tab prozess, oder?
2. **Import ins CMS**. Blöcke werden erstellt. Blocknamen persistent.
3. **Lynx fetch**:
	- **Node setup**:
		- Nodes von fetch anlegen
		- oder zu Assets matchen
		- *Johanna zu Workiva/Assets/Namen/Struktur Prozess fragen*
	- **Normalize:** Offenes JSON zu Lynx-Schema
		- Zu All body rows normalisieren.
		- Wenn header und headlines ausgezeichnet bereits zu typen normalisieren.
	- **Save all:** Alle nodes auf einmal impmortieren/speichern. Save all button machen. Speichern soll immer alle
	- **Prev year:** [[#Previous year]]
4. **Styling importieren:**
	- **Kitaco** import one click
	- **Prev year:** Import from other report
	- **Bonus:** Show styling in combined view
5. **Row typen setzen:** [[#Type tagging and toolbar features]]
6. **Zellen formatieren:** merges, current year, ausrichtungen, fettungen, indents, cell bg color, cell text color. [[#Table must-haves]]
7. **Links legen:** [[#Anchor links]]
8. **Korrekturscheifen**: [[#Populate from paste (combined view)]] and revalidate links feature.
9. **DL Table:** [[#Download table]]
10. **Backlinking:** Automatisch beim speichern wenn toggle aktiv ist
# Previous year
>[!info]
>this is to use another index as base for styling or for data (to incorporate changes into it). Was done wirh a download-upload process. Should be replaced with workiva import or new editing features like populate from paste together with update links.

>[!Warning]
>This gets conceptually complex very quickly. Keep it simple for now and mess with it the next year. Workiva import can be treated as brand new. Conventinal projects can be hard replaced. No merges. style reuses necessery yet. 
>
- Get a **various number** of indices **from another report** (same or other client)
- **Side-by-side list:**
	- **left**: current nodes (from assets, import, empty, previous year already.)
	- **right**: nodes from other report
	- **hard replace** (content and name)
	- **replace** but leave current name
	- **merge:** add pair into view: show content side by side to use populate from paste to "merge them". Then commit one of the two to replace the node.
- Button der VJ holt, nebeneinander zeigt, und man drüber befüllen kann. Oder umgekehrt, erst altes zeug holen und dann Option dass man nicht überschreibt sondern zusatzimporiert. (Befülltable). Dann beide nebeneinander anzeigen
- **Trigger:**
	- Menu on the right. Own button/list item: Put it out of uplead dropdown.
	- Or part of the index overview/assets drawer.
- **Menu**:
	- **nodes exist from Assets:** List of foreign indexNodes. Add one/more/all to current indices to replace everything but the index name.
	- **Empty:** kopiert alles (Prozess wie bisher von mir händisch)
	- ~~Line connect like at assets, then hit copy data.~~
	- ~~drag over current indexnode card?~~
	- ~~Select boxes not possible since name would have to be the same.~~
	- **Bonus:** read-only view of the indices if the old/orther report. Arrow to copy the data to the current.
# Table view
## Cell Editor
- tip tap (combined view first, we weill leave the content view as is)
- Titel markieren und zu link umwandeln: Vorteil ist, dass wenn wir Text von Ziel abweicht, dass wir dann nicht extra nachbearbeiten müssen.
## Populate from paste (combined view)
- Should often replace Excel uploads
## Create index Nodes from assets
- Also delete and rename nodes from assets?
- [ ] lynx nodes umbenennen können #JD  IMPORTANT
- [ ] sheets überall adden. #pd 
# Table paradigm must-haves
## Current year
- Needs stylesheet css
- Cell or col data on indexnode
- An custom class entry (current-year) at serialize.
- Show button in tool bar when any cell is selected to be fast
## Hover
row hover in cms like at normal tables
## Download table
Downloaden (.zip?) manuell in N:...upload/downloads legen. 
## Indents
- IndexNode: cell.indentLevel: 1 | 2 | 3 | null
- serializer: puts indent-{indentLevel} in cell.customClass
- Stylesheet comes with .indent-1 { padding-left: 8px; } .indent-2… (Can be adjusted in stylesheet ui by hand or kitaco import)
## cell bgq
- color palette icon: add color button. Actiom adds color to configNode.colorPalette (report scope): [{name: string (color 1/custom name like not material)}]. This also adds a class to the stylesheet: color-name: #123456.  
- Putting the color on a cell stores: cell.backgroundColorName: string 
- serializer puts color-name in customClass.
- Text color. Nimmt farbmame von color palette. cell.TextColorName: string. Rest wir bei bg. Farbe direkt am text wird nicht unterstützt, kann mit span.class color-name-from-palette gemacht werden. Bonus wird sein text selections zu unterstützen aber erst nach dem tip tap einbau.
## Cell indiv Font size
- Like cell bg. Statt colorPalette haben wir hier fontSizes.
- Vorteil von diesem approach: nachher flobal ändernar: eine farbe/font ändern: alles updated sich automatisch.
## List toggles
- Just html. Dont use list feature from ftl. Make html. At toggle that makes tje text content to html list (like in excel)
## Content width (nice to have)
- CmsContenWidth on report scope node
## Order and rename
- Index order am report scope node machen
## LynxReportConfig
for report scope data (mainly used by table must-haves)
- lokalen store für reportConfigs machen. Node Read. Wenn änderungen sind, beim speichern mit updaten (perform changes), sonst nicht.
# Stylesheet
- **Verions:** Stylesheet versionierbar machen.
- **PDF Stylesheet:** wird eigener node und ist dann unabhängig auch versionierbar und bearbeitbar.
- **Trigger btn:** toggle in top nav. Icon: pinsel oder darbpalette. Menu rechts, overlayed tool bar. Rechts im menü vertikale leiste wie assets zum css code toggeln (default offen). 
- **Show styling in main view:** Bonus. Daher Keine node mehr, keine route: Muss gleichzeitig zu einem index offen sein weil i optimaler weise der i dex das styling wiedergibt.
- **Converter:** kitab-config -> Lynx converter
- **Keinen visual editor.** Das in kitaco fancy machen und drauf hinverlinken oder editieren und styling importieren.
# Auto unlock
- Bei unaktivtät (nur 10 min) und wenn gespeichert ist einfach unlocken.
- in real live, people forgot to unlock indices all the time (they just closed the browser). I just had an idea i never had before: In real live a user
# Nice to have
- Rendering big indexes faster
- Restyle the link picker (keyboard nav, ...)
- real links that can be opend in new tab with strg+click
- tour zum onboarding
- info chat bot.
- Copy data from one index to anoter. User populate from paste from it. Coping from cells should add the data to the clipboard in a structured way that can be pasted into the other index.
- Wee need features to highlight all customized links (they will not follow the h1 thing)
- Service pages nicht hardcoden
- The client page should have a report cards grid where the report cards get info from the workbench about publication date and everything else thats useful to know.
- Resizeable panel
- Add btn that inserts a headline (caption) with the node name. (Type: caption)
- Nice dashboard