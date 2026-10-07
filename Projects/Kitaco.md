## Rewrite

- shadcn where possible
- react context instead of zustand

## Todo

- [ ] replacements.json gelocked
- [ ] More Settings (Dependency: Kitab)
- [ ] Sanatize inputs (zumindest auf space, das reicht shcon mal)
- [ ] More PDF settings
- [ ] Visual Editor finalization (Including PDF preview)
- [ ] Bug-fixes
- [ ] Integration tests, unit tests
- [ ] listen ?
- [ ] gerneral table font ?
- [ ] Special hover hat # davor
- [ ] Sprachen ordner: Entweder Lead sprache oben (luxus) oder alphabetisch ordnen.

### Paths
- N:\Produktentwicklung\KiTab\KiTaCo NEU\KiTaCo-Key-Revision-JW-2025_SR_Edits.xlsx

### Bugs
- [ ] Merck bug. siehe Documents → Files
- [ ] JF border color kitaco testen und sonst wolfgang ein ticket schreiben? (Jo chat)

### Nice to have
- [ ] Link auf CMS einbauen
- [ ] Jahreszahl von selbt updaten

### Notes

**Key info von Wolfgang:** https://gitlab.nexxar.com/nxrtab/kitab/-/blob/f-dms-docx-source/kitab-lib/src/site/markdown/config-keys.md?ref_type=heads

Consider to use pdf classes instead of replacements. Example:

```css
/* border only in pdf */
.profile--webpdf .table caption {
    border-bottom: 1pt solid #00194D;
}
```

### Re-style all reports
- [ ] Make list of where lynx.css is used
- [ ] Restyle on staging. Test on hippo dev tools

### Year goal
- fixes and Improvements
- New fields
- More PDF settings

### Medium term
- Finish visual editor
	- Full screen UI
	- Table preview (complex table)
	- PDF prefiew
	- Additional settings that can't be displayed visually.
- Kitaco type save machen was die config angeht.

### Long term
- Move CSS to kitaco

### Infos
- Excel overview: "N:\Produktentwicklung\KiTab\KiTaCo NEU\KiTaCo-Key-Revision-JW-2025_SR_Edits.xlsx"
- Deleted "copy from offline report" checkbox at caption and caption span. This would need snippets-css.txt parsing and the snippets may be not standarized.

### Inbetween columns missing options
chkPastcol = paste inbetween columns when creating html files
obPastesep = individual
obPasteall = global
txtPasteab = Start at column // THIS IS IMPORTANT (NOVONORDISK)
txtPastewidth = column width

### Bugs
- border-bottom-color: 00194D; kommt bei hhla rein, obwhol in kitaco keine gesezt ist, muss in kitab falsch sein
- Eine checkbox angehackt ist, wo kein farbwert drinn steht. ist aber eine, die nicht in kitaco selbst angezeigt wird (versteh das kommentar leider nich mehr ganz)

### Nice to have
- Store has immutable update issue, this must be the reason why selectors did not work. Fix this and then use fine grained selectors.
- padding boxeen gehen sich nicht aus wenn table editor eingeblendet ist.
- reihenfolge der berichte soll besser sein, aber wie?
- malta checkbox damit man tabfile name nicht 2x angeben muss.
- mit wolfgang besprechen ob wir das kitaco css nicht nach kitaco holen.

### Future
- neue features: in snippets speichern. snippets auch im kitaco bearbeitbar machen und in beide sprachen speichern. (beide sprachen wäre breaking)
- Kitaco does css
- visible editor
- Kitaco secretly takes over kitab

### Fragen
Special click - For cells with background color -> is conceptially the same as above, because hover and click is just a different state of the same element.
ú‼¶‼™Ö

### Note
replacements.json cant have tabs as indentation, only spaces work for the api response to work

### Fetch
// Need to be signed in to WB-dev
"https://workbench.nexxar.com/clients/Vonovia/reports/Annual%20Report%202020/data/kitabconfig"
"https://workbench.nexxar.com/clients/Vonovia/data/tabconfig"
jira: "https://jira.nexxar.com/browse/WORKBENCH-643"

### Deploy
jira: "https://jira.nexxar.com/browse/NXRTAB-563"

### Tasks
- Add style settings for pdf css
- Preview tables with tabstyle-pdf.css -> Add toggle in offline tables
- fix ignore first col issue - look for JW msg in PD channel

### Notes
- error: Setup threw "RangeError: Incorrect locale information provided", but no problems resulted out of that yet
- deploy: `ssh kitaco@static-int.nexxar.com` (needed initially to add host to known hosts list to make lftp connection work wich is called at `make dev`)

nslookup static-int.nexxar.com 192.168.33.28

Kitaco web app:												METRO AR 23/24

txtHlBgCo		Standard hover		Background on hover		e4f2fc		k
	chkHlBgCo
txtHlFoCo 		Standard hover		Font on hover
	chkHlFoCo
txtHlXBgCo 		Special hover		Background on hover		C8E4F9		k
	chkHlXBgCo (im kitaco oben)
txtHlXFoCo		Special hover		Font on hover
	chkHlXFoCo
txtHlMaCo 		Standard click		Background on click		e4f2fc      k
	chkHlMaCo
txtHlMaFoCo		Standard click		Font on click			1961AC		k
	chkHlMaFoCo					
txtHlXMaCo		Special click		Background on click		C8E4F9    	k
	chkHlXMaCo (im kitaco unten)
txtHlXMaFoCo	Special click		Font on click			1961AC		k
	chkHlXMaFoCo




