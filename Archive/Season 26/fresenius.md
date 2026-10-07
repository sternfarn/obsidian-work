Info:
- Role: PD
- Type: Download and cookie layer table only

Urls:
- Tnt: "https://nexxar.atlassian.net/wiki/spaces/CLIENTS/pages/242007742/Fresenius+TnT"

Prep:
- [x] Screenshot with negative numbers braced uncheckt since this is the new default -> No Screenshot used
- [x] Captions über kitaco -> Haben keine captions
[√] Checklist PD’s two cents
[√] Replace all in replacements.xlsx


TE:
mark []:
s: 		(\[.+?\])
r:		<span class="visible_html">&lt;mark&gt;</span><mark>$1</mark><span class="visible_html">&lt;/mark&gt;</span>

mark <s> (did not work automatically at TE):
s:		<s>(.+?)</s>
r:		<span class="visible_html">&lt;mark&gt;</span><mark>$1</mark><span class="visible_html">&lt;/mark&gt;</span>

delete <i>:
s:		<i><span class="visible_html">&lt;i&gt;</span>(.+?)<span class="visible_html">&lt;/i&gt;</span></i>
r:		$1