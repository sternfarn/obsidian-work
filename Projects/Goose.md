
									  🪿
!                              ~~~ G O O S E ~~~            
//                 Global Overview Of Statistical Evaluations

### Spec
Java
Matomo API
ai.nexxar.com & Matomo MCP?

### TODO
- [ ] local first. Damit dann schon auswertungen auf Anfrage machen. Simple, Node und Vite. Next.js bringt mir weniger Backend als Node. Mit diesem Node server dann andere lokale tools machen. ShadUi trotzdem verwenden. Die initiale Overview Seite selver vorrendern.
- [ ] PMs' sollen mir ein json ausfüllen. Ich stelle ihnen eines mit allen Kunden und leeren values für Kategorien bereit.
- [ ] Dann CK wegen hosting fragen

### WB
- [x] Connect kitaco-mock-server
- [x] Get clients and render them static site
- [√] Try to get reports from Matomo alone.

### Matomo
- [√] Query all clients config as static site

### UI
- [√] Add shadcn
- [√] Dark mode
- [ ] Datatable

### Node.js/Next.js
- [ ] Ask for server where i can deploy (with docker?)

### DB
- [ ] Setup SQLite DB
- [ ] On same server?

### Links
https://app.productive.io/17342-nexxar-gmbh/tasks/13172080

### Widget: Pick reports
[Client] [Report] [Start] [End] (Add)

Client  Report       Languages	Industry  Region	Index	Report type		Start					End
---WB------------------------   ---DB---------------------------------     	---WB/UI------  		---UI---
HHLA	AR/SR 2024   de, en   	Logistik  DE  	    DAX    	Full html   	Go-live/Custom Date 	Custom Date/1-12M Convenience Button   (x)


### Widget: Tag reports
Client  Report    Industry    Region	Index   Report type
HHLA	AR 2024   [Logistik]  [DE]  	[DAX]   (Save)

### Values
Industry: Branchen vom SRNAV klauen
Region: Ö/DE/SUI
Index: non-EU/DAX/MDAX/SDAX/ATX
Report type: Full html/ hybrid/ onepager

### Services
- WB (Auth, Report info)
- json file for additional Report info

### Deploy
- Ask for nexxar node.js or Docker server?
- Set up a pipeline already and leave blank where server will be. Maybe test with local server.

### Setup
- Next.js
- typescript
- Shadcn

### Paradigm
- Server first (to learn modern full stack)
- Dashboard like (To save time with ui building blocks, minimal custom styling)

### Workflow
- Auth
- Background fetch "WB" and `tags.json` and `results.json`
- Nav: "Benchmark" | "Tags"
- Benchmark: "Selection" widget
- Results_Page: Selection data (reports, data range, ...)

### Result Page
- Past results // Pannel
- Latest result is open // Main section
- If result is in progress show Skeleton in Main section
- Meta data (selected date range, selected reports)
- Charts
- Store results-{timestamp}.json