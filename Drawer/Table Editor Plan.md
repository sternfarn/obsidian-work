# Beschreibung

Mich interessiert ein Tabellen-Editor – kein Excel-Nachbau, sondern bewusst reduziert: Basic Editing (vor allem Zahlenänderungen) und einfache Strukturänderungen wie Zeilen löschen oder hinzufügen.

## Styling

Kein Styling auf Zell-Ebene. Stattdessen nur globales Styling über semantische Auszeichnungen: Was ist Header, was Body, was Fußnote. Diese Bereiche lassen sich im Tabellen-Editor optional auszeichnen. Kitaco wird entsprechend um globales Header-Styling erweitert, das dann als Override greift. Wo nichts ausgezeichnet ist, kann weiterhin Zelle für Zelle gestaltet werden – für Spezialtabellen und Ausnahmen.

Styling, das sich in Excel nicht abbilden lässt (Hover-Effekte etc.) und aktuell in Kitaco gepflegt wird, bleibt vorerst dort. Eine spätere Integration ist denkbar, für ein MVP aber nicht notwendig.

## Datenhaltung und Excel-Roundtrip

Die Datenstruktur bleibt JSON. Struktur, Styling und Auszeichnungen, die bisher im Excel lagen, werden im JSON gespeichert. Beim Schreiben eines Excels wird das im JSON hinterlegte Design angewendet: Sind globale Bereiche ausgezeichnet, entsteht ein sauber global formatiertes Excel; nur wo nichts ausgezeichnet ist, fällt es auf das Zell-für-Zell-Styling zurück.

Die Hauptaufgabe – und vermutlich der Großteil der Logik – liegt in der Konvertierung nach und von Excel. Tabellen bekommen damit grundsätzlich einen DB-/Web-App-Workflow, immer mit der Möglichkeit, einzelne oder alle Tabellen über einen Excel-Roundtrip zu bearbeiten. Dort ist weiterhin alles möglich, was bisher möglich war – man macht es aber nur noch dort, wo es nötig ist (Spezialtabellen stylen), und nicht mehr für alle Standardtabellen auf Zell-Ebene.

## Nutzen

- Kunden können direkt in den Tabellen arbeiten und einfache Änderungen selbst vornehmen. Das sollte einen Großteil der externen Tickets und späten Arbeitsschleifen auflösen.
- Mehrere Personen können gleichzeitig an denselben Tabellen arbeiten – das Tabfile ist kein Blocker mehr.
- Sauberes, wo immer möglich globales Styling.

## Specifics

- **Initial Setup:** 20k JSON Extractor. Ev. via document upload to Table Editor Web App
- **Store:** JSON am Fileserver
- **Update:**
	- WB → Kitab
	- Table Editor → (Excel) → Kitab (WB API)
- **Style:** Kitaco & Excel/JSON
- **Workflow:**
	- Kunde klickt auf Tabelle. Editor App öffnet sich. Editor app ladet Tabelle von json rein. Kunde macht eine Änderung. JSON updated sich. Excel wird erzeugt und Kitab über einen WB Endpoint gestartet. Änderung erscheint im CMS.
	- Im Table editor Tabellen parts auszeichnen können. Einbauen, dass im Excel die Info erhalten bleibt. In Kitaco/Kitab global styles einführen für header/footer styling. Header/Footer auszeichnung overrided beim Excel erstellen den stil. Wenn individueller Stil sein soll muss im JSON (Table Editor) die markierung/Auszeichnung weggegeben werden. Das Excel schreiben (vom Table Editor) verwendet styled das excel so wie im JSON vorgesehen. Kitaco Settings sollten dabei nicht gebraucht werden, weil das ja zusätzliche Sachen sind.
- **Löst:**
	- Feedbackschleifen/Externe Tickets zu Zahlenänderungen und co. die immer Stille Post und Aufwendig sind. Kunde macht es selbst
	- Excel Design Zelle für Zelle. Schnellere Style-Anderungen. Sauberes globales Styling, nur Ausnahmen werden händisch gestyled.
	- Gleichzeitig an den Tabellen arbeiten, wenn man nur einzelne "auscheckt" (als excel exportiert und importiert)
	- Eventuell: Table editor is Drehscheibe: Started 20K import und speichert Tabellen in einer Datenbank. Startet kitab anhand und gibt ihm die JSONS, sei es dass er sie temporär am file server kopiert oder als Excel konvertiert.

# Lynx Version

- JSON gerendert statt HTML eingebunden.
- Nebenbei Lynx für 20k tables fähig machen.
- Assets connection. (Offlie Assets)