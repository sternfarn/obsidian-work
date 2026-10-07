DMS replacements:
- [x] 7 Punkte für mich von hier auch mitaufnehmen https://app.productive.io/17342-nexxar-gmbh/tasks/14324948 -> Ist eh in productive
- [ ] adidas will bei z.B. auf DE KEIN Leerzeichen dazwischen haben -> Notiert

Horst der words:
Save as webpage filtered
sublime > set encoding to utf-8 oder file > save with encoding utf-8
Ornder anwählen, und nicht file. VORSICHT: Er nimmt alle unterornder und HTML files darin.
Es wird auch an die übliche Stelle gespeichert, also noch nicht unabhängig
Ergenisse an PM's rückmelden, die sollen dann entscheiden ob sie es dem kunden geben.


Vorgehensweise von Mario vorgeschlagen:
[√] yaml neu erstsellen Remove white space/nbsp between &minus and number → raushauen
[√] cms export machen und horsten. → Export content.
[√] Process development > Export content
[√] service pages nicht anhakten
[√] conversions/horst_and_hyphenations/
[√] file nur cms-xx nennen
[√] Process development > nexxtract (horst and hyühenations)
[√] cms content anhaken oder hyühenations. lest cms file aus
[√] apply. Dauert ein bissl. Am Ende soll Done stehen, davor kein Error.
[√] Schließen
[√] Dannn ist im gleichen ort ein horst file drin.

Default replacements diff machen und anschauen:
[√] phrasing text
[√] text
[√] blockqte
- [x] graphic → Findet nichts
- [x] photo → Findet nichts
- [x] link eigentlich auch? → Findet nichts
[√] Diff ev. abspeichern falls findings drin sind. 8x doppelte nowraps. 

Custom replacements file anlegen mit dingen die gefixed werden müssen:
[√] Custom yaml Erzeugen: Desc search replace.
[√] search and replace > cusotm yaml aussichen. apply.
[√] Export div mit strg + click.
[√] kommt in processing ordner

Custom horst:
- [x] Horst für custom file
- [x] kann man auf tabellen anwenden.
- [x] oder auch auf words: Words als gefiltertes html speichern, dann einmal im sublime aufmachen, als utf-8 abspeichern.

Hyphenations:
[√] hyphenations nach ausfüllen: excel > most common tools > Crete yaml file
[√] replacements > multi yaml > hyphenation replacements. Filter setzten. apply.
- [x] diff kontrollieren → nothing found in EN
- [x] save all

Custom:
- [x] + 49 (0) 91 32 84 – 0 rückwärts korrigieren https://hippo.nexxar.com/clients/adidas/ar25/de/services/impressum
[√] 8x doppelter span class nowrap raus außer. suche nach: <span class="nowrap"><span class="nowrap"> → in EN nicht nochmal gemacht, glaub ich war nicht.
[√] Horst findings
https://app.productive.io/17342-nexxar-gmbh/tasks/16220430:
[√] Then search for remaining ► in Search and edit and delete them. -> Tested
[√] überflüssige Pfeilchen raus https://hippo.nexxar.com/clients/adidas/ar25/de/an-unsere-aktionaerinnen-und-aktionaere/unsere-aktie
[√] Spans rund um die unterstrichenen Glossarbegriffe (kommen aus Workiva) https://hippo.nexxar.com/clients/adidas/ar25/de/konzernlagebericht-unser-finanzjahr/geschaeftsentwicklung-nach-segmenten/europa → Delete spans with inline style underline	<span style="text\-decoration\: underline;">(.+)</span>		$1
[√] Wenn ich wünsch dir was spielen darf..: kann man die <p>s vor dem Start der Links löschen und die gleich in den Absatz ziehen? das ist jetzt ein neues Workiva special, dass die umbrechen und ich würd sie gerne in einer Zeile mit dem Fließtext laufen lassen wie im VJ. </p><p><strong><a href="
[√] <p></p> oder <i></i> → nothing found in DE
[√] EN: <s></s> → nothing found in DE
[√] Siehe Erläuterungen zusammenziehen

Custom cleanup:
[√] EN: Doppelspaces aufräumne in EN
[√] EN: space-</strong>-space aufräumen
[√] ►

Backups:
- 21.02: before replacements
- 22.02 noon: after default replacements
- 22.02 17:45: before EN default replacements

Horst offen:
- konzernlagebericht-nachhaltigkeitserklaerung/esrs-s3-betroffene-gemeinschaften/ueberblick (,Human Rights Defenders‘ - ,HRD‘)

Findings:
- https://hippo.nexxar.com/clients/adidas/ar25/de/konzernlagebericht-nachhaltigkeitserklaerung/esrs-e3-wasser-und-meeresressourcen/kennzahlen-und-ziele: Link in FN
- komische verlinkte FN's
- Manchmal glaub ich see außerhalb vom link, aber nur punktuell.