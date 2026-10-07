> [!info] Not in confluence. Additinal personal notes.

# AI

- [x] Spin up local server → CANCELED
- [x] Connect to `ai.nexxar.com`

> [!info] Consider
> Report AI interessant für Lynx?

# Code Quality

- [x] Einheitliche convention filenamen und ordnerstruktur. filenamen index?
- [ ] Lazy load excel js to satisfy build.rolldownOptions.output.codeSplitting
- [ ] Why does it print "delete index did not work" so often even though i haven't clicked it
- [ ] Why is ConfigDataPage.tsx not used?
- [ ] Überall clsx verwenden und die spaces wegbekommen
- [ ] make more functions in hooks so that they do not always run
- [ ] Translations are done on multiple places. (_getTranslation, ect...) make one file in src/utils
- [ ] A indicator should not have children []. normalize them away (Localhost Geberit kurzer Index glaub ich wars)
- [ ] Does FlatIndicator really need a level property?
- [ ] remove level from Structural, Indicator, and Footnote and use FlatStructural, FlatIndicator, and FlatFootnote whenever level is needed
- [ ] Performance: useVersions renders to often (seen at the console log), does it really need to import the id just to log it?
- [x] switch to flat data structure to enable seperators as indication where to split a index into additinal multiple read only blocks and also to enable changeable headline types like h2, h3, or caption.
- [ ] is there a way to detect if the browser is still painting to show the skeleton until indexNode render is done → Tried it, but found nothing that made it work so far
- [ ] Copy button at stylesheets css editor for consistentcy since the index data can also be copied

# General

- [ ] lynx uhrzeiten 2 off (jetzt im sommer) - richtig stellen
- [ ] FTL: { "type": "text", "title": "<ul><li>...</li></ul>", "bold": false, "target": false } Passt soweit, aber im CMS kommt dann ein p vor und nach der liste rein (JM, GRI). War aber nur bei der händisch mit html gemachten liste der fall. Wurde dann als lynx list gelöst
- [ ] italic in toolbar (jm)
- [ ] dnd stört ein bisschen weil man nichts markieren kann. fühlt sich ein bissl distant an dann der content. besser dnd mit toggle erst aktivieren.
- [ ] Ai Tests schreiben
- [ ] Internal links: Bei redirect vorschlagen dass es den link auf die nächste page nimmt aber den text vom redirect. Damit nachher die backlinkks auf der pagee liegen können. Da wird dann auch der nächste Punkt aktiv

```ts
node {
	... on PerPageProperties {
		page_redirect
	}
	...
}
```

- [ ] Internal links: Link symbole sollen anzeigen wenn der titel modifiziert ist. Zb ein kleines T dazu oder sowas. Ebenso wenn pre und post verwendet wurde das verweden. Und redirect links sollen einen pfeil oder so als icon haben.
- [ ] stylesheet: inbetween min width 8px
- [ ] Built in index class that makes font smaller. Similar to mega.
- [ ] Jeder index sollte eine id bekommen damit man auf ihn einen ankerlink setzten kann und nicht erst eine id in die überschrift hineinquirken muss, wenn er zb als block irgendwo im content vorkommt
- [ ] headlines should become an id.
- [ ] Backlinking sprachspezifisch machen (VIG). Wenn Backlinks nicht nur "1-1" lauten sondern customized werden , zb. so: "Ökonomische Inddikatoren", dann muss es sprachspezifisch werden. Dazu braucht es Lynx (erstellen), FED (auslesen), und den CMS-Editor (auswählen). Im CMS Editor soll dann zB. zusätzlich zu gri und esrs auch mutlilang zum auswählen sein.
- [ ] Bei voest hat sich das kapitel geändert, scheint nicht bei revalidate links auf. Muss man dann händisch machen
- [ ] Languge switch hat in der Indexoverview keinen effekt. Ausblenden.

# Bugs

- [ ] Voest: englisher text noch leer. ich klicke auf das leere item, popover kommt, ich möchte text reinpasten aber nichts passiert. Also schalte ich auf DE um, öffne dort das Text popover, paste dort den text in das englische Feld, und dort gehts. Beim nächten index ging aber dann wieder alles. komish.
- [ ] Bug: Manchmal geht strg+f nicht
- [ ] #omv_bug JD wegen dieser komischen OMV Seite fragen https://hippo.nexxar.com/clients/omv/ar25/en/directors-report-sustainability-statement/esrs-2-general-information/esrs-index-and-datapoints-from-other-eu-legislation
- [ ] Bug: Multiple col spans in one indicator row do not work. It is the same bug as there was at the rowspan (which is fixed), where every additional rowspan destroyed the ones in place.
- [x] Bug: Row id was not unique ([Sandvik](https://hippo.nexxar.com/clients/sandvik/ar25/en/sustainability-statement/sustainability-appendix/esrs-content-index)) [6. märz 2025](https://chat.nexxar.com/nexxar/pl/j4f986jfnbnntexhciha8hwejr) → *Konzeptionsproblem, kein Technisches. Gleicher Link Und gleiche Beschreibung, was soll es da unterscheiden... Bräuchte Info von Überschrift/Section, und in die backlink namen die überschrift auch dazu, damit der user sieht dass es verschiedene links sind (bzw. dass der link in verschiedenen secions vorkommt).* **Trotzdem: Row id override machen, zu row class dazu oder so.**
- [x] *Bug: The incremental counter for non-unique backlink IDs (GRI 3-3) did not work correctly across sections. The count always reset to 3-3-01 instead of incrementing to 3-3-02, 3-3-03, etc. ([Merck](https://hippo.nexxar.com/clients/merck/ar25/de/weitere-informationen/gri-inhaltsindex))*
- [ ] Bug: Download merged cells error. Albert chat: "Gibt einen Bug mit Excel-Download von Zellzusammenfassungen". It increments correctly from row to row, but within a row the running number is not updated.
- [ ] Bug: (could not reproduce so far): After copying text and opening the link menu in between, paste no longer works, even after copying again. A page refresh does not resolve the issue. The console shows: "no clipboard provided".
- [ ] Bug: Link title has too many spaces. Reproduce: Look at lynx > data > serialized index node and scroll to a internal link title. Example: "title": "Allgemeine Informationen  / Berichtsgrundlagen  / Berichtszeitraum und Berichtszyklus". The cms lynx render templated fixes it, so it is correct in the CMS.
- [ ] Bug: Put a single table line at the very bottom. In the CMS it will be part of the preceeding table, even if this is nested. It was not reported yet, but it could happen. Adust serialization logic to only wrap the row if it's a direct sibling.
- [ ] BUG: Recently used colors does not work (low)
- [ ] Wenn man in pre entf drückt löscht man das item, vl. auch pre post. Ah ist nur ein folgefehler von was. nach laden gehts wieder
- [ ] I had a paste issue, paste in the link dialog pasted the whole link. the old issue. it happend at beiersdrof ersr c when chanting ESRS E1 Linktext. (Stefan)

# Navbar

- [ ] UX: language switch click area ist zu klein. Wenn man auf den Leerraum zwischen den beiden sprachen klickt soll es auch umschalten, nicht nur wenn man eine Sprache erwischt. (low)
- [ ] UX: Versions overview should rerender after save so that new version is imeditally visible, not after refresh. (low)
```ts
query versions($id: ID!) {
  editable(id: $id) {
    ... on lynx_config {
      linearVersionHistory {
          ... on NodeInfo {
            nodeId
          }
        }
      }
    }
  }
}

oder

query versions($id: ID!) {
    editable(id: $id) {
      ... on lynx_config {
        lastChangedTime
        linearVersionHistory {
          nodeId
        }
      }
    }
  }



{"id":"2fa1248d-5400-43b6-be9d-14e5fccbfd11"}
```
- [ ] UX: alt+enter soll auch new line machen, nicht nur shift+enter, weil man ist es vom Excel so gewohnt. (high)
- [ ] When closing the browser while beeing on the index, there is a browser warning. The warning is meant as  a reminder to close the index (navigate back). But it is missleading since the browser message can't be modified and it always says "unsaved changes might be lost", wich is the wrong message. Better remove this warning. Only keep it when the work is really unchanged, wich works already.
- [ ] Externer link oder service page nimmt mailto nicht. haben es bei jm jetzt als text gemacht. da gehts.

# Footnotes

- [ ] Footnote text changes are currently not undoable but should be. (high)
- [ ] Fußnotenzahl ist mittig ausgerichtet → oben ausrichten. (high)

```ts
{
	 "type": "footnote",
	 "footnoteRows": [
			{
				"id": "",
				"reference": null,
				"text": ""
			}
	 ]
}

<table class="lynx__footnote-table">
	<tr class="lynx__footnote-row">
		<td class="lynx__footnote-reference">{reference}</td> <!-- only renders if reference is not null -->
		<td class="lynx__footnote-text">{text}</td>
	</tr>
</table>
```

# Misspellings

- [ ] "...to enable quick access in the CMS" → "...to enable quick access to the CMS"
- [ ] "Report page" → "Back to report page". Otherwise it seems like you can "report" something.

# Notes

- Check out Sandvik styling, the gaps are weird
- in branch 'slate' are dashboard design changes to more modern design

# Autosave drafts

- [ ] https://nexxar.atlassian.net/browse/NXRCMS-4858
- [ ] Save drafts (does it already happen with perform changes). If so, ask how to fetch an editable instead of the index. Bei starutnia nachascheuen
- [ ] Was ist canEdit und das zeug beim editable? Look in Saturnia. If not find it, just leave it for now
- [ ] If not needed delete it from query

# Design

Combine second and third nav bar.
make background of all navbars light grey.
Structure: Remove the grey lines

# Eigene Ideen

- structure actions wie zeile löschen in ein und derselben view wie content doch sinnvoll, damit man zb wie bei bechlte wo nur links drin sind nicht abzählen muss, weil links nicht ausgeschreiben sind. ok ist scheingrund, man könnte links auch ausschreiben in der structure view.
- baseUI toast einbauen

# Mock server

- [ ] mock add index
- [ ] mock unlock index
- [ ] mock dispose editabel
- [ ] mock delete index

# Packages

- [ ] Upgrade to tailwind 4 (latest) and get rid of glob override in package.json
- [ ] 'react-hooks/react-compiler': 'error' geht nicht mehr, warum?

# Folder structure and naming conventions
- [ ] Move everything from components to the features and only lift as high up as needed
- [ ] Harmonize file names

# Linked footnotes

## Marker

- [ ] Introduce Footnote item: This will be the marker in the text flow. "*"
- [ ] id: "fn-1-marker" // `#fn-${translMarkerTitle}-marker`
- [ ] href: "#fn-1-footnote" // `#fn-${translMarkerTitle}-footnote`
- [ ] language specific aria-label: "Springe zur Fußnote 1" // `${transFootnoteAriaText} ${translMarkerTitle}`
- [ ] FTL renders marker: examples/linked-footnotes.notes#Marker
## Footonte

- [ ] language specific aria-label: "Zurück zur Fußnoten-Referenz"
- [ ] href: "#fn-19-1-1-marker"
- [ ] FTL renders footnote: examples/linked-footnotes.notes#Footnote

# Resuse used links

There should be a pool of used links to choose from. When the same modified link is needed again, currently the user has to find and copy it.
- Maybe change the whole structure so that links point to a link in this pool. And the pool is updated an every link update.
	The link pool does store all info including original title, pages is dynamic and can change an every load, as of now.
- Or derive used Links. Filter links by checking the equality of all fields.

# Stylesheet view

1. Wireframe editor to click and edit
2. Accordeon Editor stays the same
3. Raw css editor stays the same
4. Preview of a short mock data index

# Flat structure

- caption einfach als h8 (untersete ebene) behandelne, weil unter einer caption erwartet man immer die tatsähcliche tabelle.
- Die flat migration wann dann hard machen. neue schema version angeben. alles was älter ist zu dieser convertieren. diese hardcore flat machen. rows einzeln, fields einzeln, items einzlen. alles nur über ids verknüpfen, bei möglichen mixed tpye arrays (rows, items) muss type angegeben werden. zb. field { items: [{ type: 'text', id: '1' }, { type: 'internal-link', id: '1' }] }. Bei felder ist es so. row { fieldIds: ['1', '2', '3'] }. Text updaten geht dann ganz einfach, es wird im text array nach der id gesucht und der title upgedated. kein tree iterieren mehr notwendig.

# Paste to populate

- tabellen aufbauen in lynx, kein excel upload notwendig, würde tabellen befüllen vorbereiten. Nämlich folgend: Wenn tab seperated und new line seperated text gepasted wird, splitte new lines in zeilen und tabs in zellen und baue den index damit auf.
- es wird reiner text gepasted, somit wird eine caption zunächst eine zeile mit nur einer zelle. die kann man dann umstellen zu einer caption, als würde man tabellen stylen.
- wie tun wenn man VJ neu befüllen möchte? geht wegen links nicht. ev link spalte übrig lassen. und nur mit update links von ar25 zu ar26 updaten.
- header in seperatem bereich befüllen
- headlines wird zunächst indicator row aber kann converted werden (mit den buttons in der toolbar) zu headlines. Da wird dann einfach der Inhalt der ersten Zelle genommen.
- eine leere index seite soll ein file drop box haben, und eine templating box zum frisch starten. und ev eine befüll box.

# Combined view

- fürn header in der neuen combined view auch ein normales text edit feld machen

# Utiltiy classes

css global und index level. zellen level utitlity calsses. Esrt einfach mal zusätzlich anbieten. soll dann mehr und mehr verwendet werden statt selbst geschreibenene special classes. Herausforderung: was wenn mehrere klassen drauf sind und man wieder was wegtoggeld? Antwort. center toggle darf zb nur text-center wegtoggeln bzw stattdessen text-right reintoggeln. text left wird es nicht geben. da greift einfach das default css. ok , d.h. die utitlity classes müssen UNTER dem default css sein. beim saven soll es unten fixiertes utitliy css anhängen.
Bonus: stelle das styling in lynx schon da, schriftgröße und alles. toolbar schreibt utility classes rein. kann man auch händisch reinschreiben. ftl soll sie dazurendern.

# Unclear

- bei anchor id's handeln wenn nur eine sprache vorkommt
- nice to have ui: copy to clipboard einbauen.
- beim download wenn möglich überschriften kenen textumbruch geben
- Borders utitlity classes. ein usability voretil wäre gegenüber excel wenn es partielle farben auch kann.
- neue structure view einführen und darin sortable probieren, diesmal aber nicht als page sondern nur so, weil dann rendered es vl. schneller. hätten wir zb bei omv iro gebrauch wegen dem tag

# Upload download

- `C:\Users\StefanR\Documents\files\lynx\upload\needs-fix\hhla-with-no-space-in-empty-subheadlinest.xlsx`
- `C:\Users\StefanR\Documents\Lynx\files\upload\intentional-errors\___empty-cell_-_use-case-basf-_-UNHANDLED.xlsx` → But lower levels CAN be empty. Look at hhla import.
- **Easy solution:** Make seperate download where the whole cell json is pasted instead of the extracted text. Solves heavy mutations. Does not solve defered second lang implementation.
- **Better solution:** Store cell json in cell comment. At upload merge title in cell json. Solves everything exept column widhts. Columns withds could be stored in header cell comment.
# Design

in nem reinen Textblock ist der Zeilenabstand 2 oder 3 px, in nem gemischten ist er 1 oder 2 (ist jetzt abgeschätzt, kleiner halt) https://chat.nexxar.com/nexxar/pl/eq66aii6t7f1jynea7s788b7tr
auf dashboard die pfeilchen löschen, schauen aus als könnte man sie aufklappen.
Loading locks in index overview (report page) should show "ceck locks..." otherwise it looks like the index itself is loading. Display text checking for locks next to loading symbol (Stefan)
Link picker: Less padding between links/pages. Especially between folder and pages block underneath
Design wie ich es mit abstand erwarten würde. Downoda rechts oben
Unter hedaer ist ein kleiner gap before dann die nächste navbar zbw. der background anfängt

# UX

- [ ] Sticky headlines

# Workflow

Redo BASF and reuse AR25 to pseudo AR26. Make good reuse prior year workflow. Download  Ziel: Texte aktualisieren, damit man nich optisch vergleichen muss. Links aber stehen lassen und updaten, update link targets notification anzeigen wenn es alte document urls entdeckt. Partiell befüllen online oder klassisch mit download. Teste nochmal als würdest du BASF neu machen. Downloade esrs datapoints, haue neue inhalte rein, vl. neue zeilen, dann uploade es wieder. Das muss gehen. Das ist minimalanforderung.
übersetzung bei bechlte war händische arbeit, geht es besser? Nochmal probieren, diesmal mit download upload

# Rest

Is there a way to paste columns from one index to another → No, lot's of logic for different structure needed

- Header individuell in content view ändern? Wird glaub ich nicht wirklich gebraucht
- bei search and replace ein regex bottom menu machen wo man regexes vom master anwählen kann und diff vorschaut im content hat wo man durchscrollen kann und sieht wie es aussehen würde. man kann auch mehrere anhaken, dann sieht man sozusagen gleich den endstand als vorschau. und man kann auch die reihenfolge ändern der regexes sodass was anderes vorher matched. Wenn das klappt dann eine eigene route machen zu der man von der rott aus am dashboard mit einem button hinkommt. der button heißt search and replace. Und dort kann man selber texte reinpasten.
- darstellung im content soll auch schon ein bissl mehr den style beachten wie zb bei bechlte datapoints listenpunkte zentriert. Vielleicht könnte in der toolbar ein toggle zur ausrichtung eine utitlity class in die zelle schreiben "text-center". Vl generell mit utitlity calsses mehr arbeiten. 
- PM channel: https://chat.nexxar.com/nexxar/pl/w8ntxa69ffdabbia5n5th9rzdc
- unique linklist eventuell beidsprachig aber andererseits völlig fürn arsch
- Colspan in header should be visible
- Ask: Fritz, Melanie Ivana and more? for feedback. Unintuitives handling, was fehlt noch um es dem kunden zu geben?
- ev. drag and drop mit switch aktivieren, ansonsten hairline cursor anzeigen. ist vl. angenehmer im handling, weil dnd brauch man eh so selten. Wurde mittlerweile aber schon gebraucht. Vl. lieber auf sortable umstellen nur innerhalb der zelle zbw paragraphen? Wobei die beschränkung muss man auch mal checken. hatten wir ja schon und hat mich ja so gestört.
- Texttables
- Glocke mit 1er oder 2er machen. und dropdown mit item "update link paths from prior year to this year" (wenn man altes jahr importier hat, und es detected dass noch ar24 vorkommt) und mit item "update link titles after cms title change" wenn sich im cms titel was geändert hat. Und drittes item hinzufügen: "update link urls after cms url change". Um das zu detecten einfachs chauen ob wir die verwendetetn document urls anders sind als von den aktuellen pages.

Local storage
```ts
[
	{
		"client": "Geberit",
		"report": "Annual Report 2022",
    "reportId": "0c5416aa-080c-467f-ab57-8d7377067a98",
		"indexNode": "ESRS",
		"indexNodeId": "sadfsdfsadfsdaf"
  }
]
```


# Paragraphs

+ some import now, like adidas, would benefit from supporting paragrpahs for initial import
- Supporting paragraphs is error prone since users can change order or forget new lines in other lang and then everything breaks.
+ Added check if pars match between languages
- But if pars change it does not match with data structure from note anymore. Would need also check.
- No one ever complained about paragraphs beeing not imported. People can devide it in lynx. The lynx UI is made better for a reason.

# Autosaved optimized (optional)

- On Mount: check if draft is newer, if so mark unsaved. // Will start autosave
- Autosave: Every 10 seconds check if unsaved is marked and if so save draft.
- On client side change: Mark unsaved (already does)
- On save: mark is saved // (Autosave will stop
- Optional UX: Show short sync indication every 5 seconds. Persistend "draft" button would be subset of Asterisk.
- On Release: Warns if marked unsaved. Discard draft. Reset Asterist (all stores). Leave route.