---
{"dg-publish":true,"permalink":"/cjca/linux/regex/","created":"2026-04-12T11:01:28.055+01:00","dg-note-properties":{}}
---

Regular expressions (`RegEx`) are like the art of crafting precise blueprints for searching patterns in text or files.
==At its core, a regular expression is a sequence of characters and symbols (metacharacters)that together form a search pattern.==
<mark style="background: #FF5582A6;">metacharacters</mark> allow us to specify whether you're searching for digits, letters, or any character that fits a certain pattern.

## Grouping
Regex offers us the possibility to group the desired search patterns. Basically, ==regex follows three different concepts, which are distinguished by the three different brackets:==

| operators | Description                                                                                                                                                                                                               | Examples:                                                                                                                                                                                                             |
| --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `(a)`     | The round brackets are used to group parts of a regex. Within the brackets, you can define further patterns which should be processed together.<br><br>Used for **capturing** (to reuse later) or controlling precedence. | (PermitRootLogin) matches the entire word and captures it.<br><br>                                                                                                                                                    |
| [a-z]     | The square brackets are used to define character classes. Inside the brackets, you can specify a list of characters to search for.<br><br>Matches any *lowercase letter*                                                  | Example: `[abc]` matches `a`, `b`, or `c`<br><br>`[Permit]` matches any single character: `P`, `e`, `r`, `m`, `i`, or `t`                                                                                             |
| {1,10}    | The curly brackets are used to define quantifiers. Inside the brackets, you can specify a number or a range that indicates how often a previous pattern should be repeated.                                               | Examples:<br><br>- `a{2}` → matches `aa`<br>    <br>- `a{2,5}` → matches `aa`, `aaa`, `aaaa`, or `aaaaa`<br>    <br>- `(abc){2}` → matches `abcabc`<br>    <br>- `[0-9]{4}` → matches exactly 4 digits (e.g., a year) |
| \|        | Also called the OR operator and shows results when one of the two expressions matches                                                                                                                                     | (Permit\|Allow) matches permit or Allow                                                                                                                                                                               |
| .*        | Operates similarly to an AND operator by displaying results only when both expressions are present and match in the specified order                                                                                       | (Permit.*Allow) matches bothpermit and Allow                                                                                                                                                                          |
<mark style="background: #FF5582A6;">need to apply the extended regex using the `-E` option in grep.</mark>

###### Exercise:
use the `/etc/ssh/sshd_config` file on HTB pwnbox

| N   | Task                                                                   | Result                                                                                              | Note                                                                                                                                                 |
| --- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1   | Show all lines that do not contain the `#` character.                  | `grep -v "[#]" /etc/ssh/sshd_config`                                                                |                                                                                                                                                      |
| 2   | Search for all lines that contain a word that starts with `Permit`.    | `grep -e "(\bPermit\w*)" /etc/ssh/sshd_config`                                                      | If using boundary with regex:<br>`'\bPermit\w*'`<br><br>==\b starts the boundary, permit is the pattern looking for, \w* matches evertything after== |
| 3   | Search for all lines that contain a word ending with `Authentication`. | `grep -E "(Authentication$)" /etc/ssh/sshd_config`                                                  | `AUthentication$` to specify the pattern end.                                                                                                        |
| 4   | Search for all lines containing the word `Key`.                        | `grep "Key" /etc/ssh/sshd_config`                                                                   |                                                                                                                                                      |
| 5   | Search for all lines beginning with `Password` and containing `yes`.   | `grep -E "(Password.*yes)" /etc/ssh/sshd_config<br>`                                                | same as : `'(\wPermit\w*.*yes)'`                                                                                                                     |
| 6   | Search for all lines that end with `yes`.                              | `grep 'yes$' /etc/ssh/sshd_config<br>`<br>The `$` is a regex anchor that denotes the end of a line. |                                                                                                                                                      |

###### What I learned?
==Regex anchors:==
A **regex anchor** does not match any character.  Instead, it matches a **position** in the string, such as:
- the start,
- end,
- or word boundary.

	- `^` — Start of string (or line in multi line mode)  
	    Example: `^Hello` matches lines starting with "Hello"
	
	- `$` — End of string (or line)  
	    Example: `world$` matches lines ending with "world"
	
	- `\b` — Word boundary (between `\w` and `\W`)  
	    Example: `\bword\b` matches "word" but not "keyword"
	
	- `\B` — Not a word boundary  
	    Example: `\Bend\B` matches "bend" in "lending"
	
	- `\A` — Start of string only (ignores multiline)
	
	- `\z` — Absolute end of string (no exceptions)
	
	- `\Z` — End of string, or before final newline 


Anchors are **zero-width** — they assert position without consuming characters.