
Always do this (approved and also tested by myself)
Zahl und Wort und Wort (nur große Anfangsbuchstaben) und Zahl
- Numbers (except 4 in a row or with a closing tag in front) followed by withspace but not standard word list
	- S:    ``(^|[^\d/>])(\b(?!\d{4}\b)\d+\b) \b(?!Mill)\b``
	- R:    $1$2<span class="visible_html">&amp;#160;</span>$3
	- example: 32 employees
 - Numbers (except 4 in a row) preceeded by a word starting with big Initial and whitespace
	- S:    ``(^|[^\d/>])(\b[A-Z][a-zA-Z]*) (?!\d{4}\b)(\d+)``
	- R:    ``$1$2&#160;$3``
	- example: Level 1

