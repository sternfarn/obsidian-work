- Jo feedack: telekom 8 blöcke anstrengend. (column breite anpassen, ...) → Mein takeaway: Das ist ein Fall wo die indexe gleich sind, so als wäre es ein großer, daher muss er acht mal genau das gleiche machen. → Batch editing für mehrere blöcke machen? Alle blöcke eines Berichts öffnene können. Sie werden untereinander angezeigt. Lazy load natürlich. Bulk edit. This Foundational investment builds Strategic groundwork for for future proof indexes that might as well be used mass tables. → Stichwort "Multi-index editing"
-	albert hatt bei vw auch das gleiche, dass er 15 blocks oder so hat die alle fast gleich sind. Überlegen wie wir hier alle blocks auf einmal anlegen, und bearbeiten können, so als wäre es ein großer index. gespeichert werden die parts natürlich trotzdem als block.
-> IDEE: Man legt tatsächlich einen großen bolck an, der kann sogar als ganzes eingebunden werden. Aber man kann ganz generell bei indexes trenner reingeben. oder scopes. oder Additinal blocks border. diese Fragmente bekommen einen namen (bock name). Beim speichern wird zusätzlich zum normalen speichern des indexes für jedes fragement ein block erzeugt oder upgedated. BUMM!
-> Bessere Idee: Gruppen. Eine Gruppe ist am server ein IndexNode. Aber seine config besteht aus einer overview über blocks. Wenn man eine Gruppe öffnet kommt eine neue spezielle view in der alle blocks und gruppen options zu sehen sind. Man kann die reihenfolge ändern, zukünftig gruppenweise importieren und alle blocks in einer gruppe auf einmal speichern (inkl der gruppe selbst). column settings in der gruppe, setzten sie auf jeden block. Gruppenansicht ist anders: Eine geöffnete Gruppe zeigt sich entweder wie ein tabfile (overview und durchblättern), oder besser, gruppeninfo ist links im burger menü. ist wie ein inhaltsverzeichnigs. Und alle blöcke sind untereinander mit lazy load. links hin und her kopieren wird somit möglich. Es können auch nachträglich blöcke in gruppen eingefügt werden: Die info ist one way. die gruppe muss nur wissen welcher block zu ihr gehört. für einzelne blöcke selbst ändert sich nichts, die verhalten sich selbstständig wie blöcke.
	-> Problem: Warte, was ist im arbeitsspeicher/store wenn man ein egruppe offen hat? Es wird dann ein bisschen wie früher mit riesen store wo man immer aktuellen index selecten muss, oder?
### 	-> Blöcke einbinden dauert trotzdem lang, aber da kommt man nicht drum herum. Ah doch: es sollen einen combined index mitspeichern. also
	IndexGroup: tracks indexNodeIds[] and has options. Has also a output field with the output of all blocks it groups. Or better: the group itself has the merged other blocks as its own content.

### Split index
	i leave the schema but renam indeNode to basenode and reduce my typesctip types a bit and thahn on top of that i will do GroupNode (need a good name: CompositeNode, CompNode, WrapperNode, GroupNode, CollectionNode)
	"Group A" ( type BaseNode.CollectionNode)
		"Index A.1" (type BaseNode.IndexNode)
		"Index A.2" (type BaseNode.IndexNode)
	"Index outside of Group"
	"Group B"
		"Index B.1"
	
	every BaseNode already has a "output" property. His is what the block in the cms renders.
	Group blocks should use this property to merge the child blocks and store them in its output.
	in the cms the user sees this list of all nodes, and can select a group node for minimal effort if he needs all of the indexes one after another, or at other places of the cms where he needs them isolated he can just pick the single index.
	"Group A" 
	"Index A.1"
	"Index A.2"
	"Index outside of Group"
	"Group B"
	"Index B.1"

The table mindst does not need a combined output not on indexCollectionNode.

No, this gets to complex. Just make a big index when you need it. and when you need parts of it additionally, create a method to give the user ui to place seperators, and implement a function on save, that does not only save the big index, but also creates a indexnode for every fragment, and maybe gives it a lock, so that the source of truth stays the big index, and the single blocks are never touched. but technically of course, the big index and the single block are the same kind of node (indexNode.) i just use them differetnly in the ui. What do you think about it?
"GRI" (IndexNode) Place seperators. onSave creates a block for every segment
"GRI A" (IndexNode, derived: not editable)
"GRI B" (IndexNode, derived: not editable)

- [ ] das update link tool in lynx ist derzeit schwierig zu interpretieren für mich: werden da namen von Seiten aktualisiert, deren URLs es aber gar nicht mehr gibt? Hm, habe iwie den Faden etwas verloren.

- [ ] Wenn du bei lynx noch keine Anker einträgst, aber (weil du 3x in das Detailmenü für den Link musst), schon mal die Ankerverknüpfung rausnimmst und dann Done drückst, speichert es die Einstellung für den nicht-verbundenen Anker nicht. (Albert)

### Prio
anker
Reuse prior year: Update links
Split index
headline type: h2/h3/.../caption ändern können
session, autosave draft, no data loss
Stylesheet improvements
xlsx improvements
other ux improvements