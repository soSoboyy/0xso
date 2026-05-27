---
{"dg-publish":true,"permalink":"/0x/htb/cjca/bash/bash/","created":"2026-05-13T06:13:36.027+01:00","dg-note-properties":{}}
---

```bash
#!/bin/bash
# Check for given argument 
if [ $# -eq 0 ] 
then 
	echo -e "You need to specify the target domain.\n" 
	echo -e "Usage:" 
	echo -e "\t$0 <domain>" 
	exit 1
else 
	domain=$1 
fi

```
- `#!/bin/bash` - Shebang.
- `if-else-fi` - Conditional execution.
- `echo` - Prints specific output.
- `$#` / `$0` / `$1` - Special variables.
- `domain` - Variables.

######  Shebang
The shebang line is always at the top of each script and always starts with "`#!`". T*his line contains the path to the specified interpreter (`/bin/bash`) with which the script is executed*. We can also use Shebang to define other interpreters like Python, and others.
`#!/usr/bin/env python`

###### If-Else-Fi
Checking of conditions usually has two different forms in programming and scripting languages, the `if-else condition` and `case statements`. In pseudo-code, the if condition means the following:
```bash
#!/bin/bash
if [ the number of given arguments equals 0 ]
then
    Print: "You need to specify the target domain."
    Print: "<empty line>"
    Print: "Usage:"
    Print: "   <name of the script> <domain>"
    Exit the script with an error
else
    The "domain" variable serves as the alias for the given argument finish the if-condition
```

By default, an `If-Else` condition can contain only a single "`If`", as shown in the next example.

==if-only.sh==
```bash
#!/bin/bash

value=$1
if [ $value -gt "10" ]
then
	echo "Given argument is greater than 10."
fi
```

execution:
`bash if-only.sh 5`

```shell
#!/bin/bash
sosoBoy@htb[/htb]$ bash if-only.sh 12 

Given argument is greater than 10.
```
###### if-elif-else
When adding `Elif` or `Else`, we add alternatives to treat specific values or statuses. If a particular value does not apply to the first case, it will be caught by others.

Several Conditions - Script.sh
![Attachments/Pasted image 20260513051334.png](/img/user/0x/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260513051334.png)
