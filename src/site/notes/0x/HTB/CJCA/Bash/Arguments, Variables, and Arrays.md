---
{"dg-publish":true,"permalink":"/0x/htb/cjca/bash/arguments-variables-and-arrays/","created":"2026-05-14T06:47:14.515+01:00","dg-note-properties":{}}
---

#### Arguments

The advantage of bash scripts is that we can always pass up to 9 arguments (`$0`-`$9`) to the script without assigning them to variables or setting the corresponding requirements for these.
==`9 arguments` because the first argument `$0` is reserved for the script.==
 we need the dollar sign (`$`) before the name of the variable to use it at the specified position:

`sosoBoy@htb[/htb]$ ./script.sh ARG1 ARG2 ARG3 ... ARG9        ASSIGNMENTS:       $0      $1   $2   $3 ...   $9`

<mark style="background: #BBFABBA6;">This means that we have automatically assigned the corresponding arguments to the predefined variables in this place.</mark> ==These variables are called special variables.== <mark style="background: #FF5582A6;">These special variables serve as placeholders. </mark>

**Special variables** use the [Internal Field Separator](https://bash.cyberciti.biz/guide/$IFS) (`IFS`) to identify when an argument ends and the next begins. Bash provides various special variables that assist while scripting. Some of these variables are:

|**Special Variable**|**Description**|
|---|---|
|`$#`|This variable holds the number of arguments passed to the script.|
|`$@`|This variable can be used to retrieve the list of command-line arguments.|
|`$n`|Each command-line argument can be selectively retrieved using its position. For example, the first argument is found at `$1`.|
|`$$`|The process ID of the currently executing process.|
|`$?`|The exit status of the script. This variable is useful to determine a command's success. The value 0 represents successful execution, while 1 is a result of a failure.|
#### Set Execution Privileges: 
`sosoBoy@htb[/htb]$ chmod +x cidr.sh`
- ###### Execution without Arguments : `sosoBoy@htb[/htb]$ ./cidr.sh`
- ###### Execution without Execution Permissions : `sosoBoy@htb[/htb]$ bash cidr.sh`

Check this code snippet:
![Attachments/Pasted image 20260514053310.png](/img/user/0x/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514053310.png)
==we have 3 such special variables in our `if-else` condition.==

| **Special Variable** | **Description**                                                                                                                                                                                                                                       |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `$#`                 | In this case, we need just one variable that needs to be assigned to the `domain` variable. This variable is used to specify the target we want to work with. If we provide just an FQDN as the argument, the `$#` variable will have a value of `1`. |
| `$0`                 | This special variable is assigned the name of the executed script, which is then shown in the "`Usage:`" example.                                                                                                                                     |
| `$1`                 | Separated by a space, the first argument is assigned to that special variable.                                                                                                                                                                        |
We also see at the end of the if-else loop that we assign the value of the first argument to the variable called "`domain`". ==The assignment of variables takes place without the dollar sign (`$`).== <mark style="background: #BBFABBA6;">The dollar sign is only intended to allow this variable's corresponding value to be used in other code sections.</mark> **When assigning variables, there must be no spaces between the names and values.**
```bash
#!/bin/bash
else
	domain=$1
fi
```

In contrast to other programming languages, t<mark style="background: #FF5582A6;">here is no direct differentiation and recognition between the types of variables in Bash like "`strings`," "`integers`," and "`boolean`." </mark> **All contents of the variables are treated as string characters.** Bash enables arithmetic functions depending on whether only numbers are assigned or not. **It is important to note when declaring variables that they do `not` contain a `space`.** Otherwise, the actual variable name will be interpreted as an internal function or a command.
###### Declaring a Variable - Error
```bash
sosoBoy@htb[/htb]$ variable = "this will result with an error." 

command not found: variable
```
<mark style="background: #FF5582A6;">NOTE: This contain many space so it returns error.</mark>
###### Declaring a Variable - Without an Error
```bash
sosoBoy@htb[/htb]$ variable="Declared without an error." 
sosoBoy@htb[/htb]$ echo $variable 

Declared without an error.
```
<mark style="background: #BBFABBA6;">NOTE: No space in here</mark>

---
#### Arrays
There is also the possibility of assigning several values to a single variable in Bash. This can be beneficial if we want to scan multiple domains or IP addresses.
- These are called **arrays**
- They store an ordered sequence of specific value types
- Index starts at 0

arrays.sh
```bash
domains=(www.inlanefreight.com ftp.inlanefreight.com vpn.inlanefreight.com www2.inlanefreight.com)

echo ${domains[0]}
```
We can also retrieve them individually using the index using the variable with the corresponding index in curly brackets. *Curly brackets are used for variable expansion.*

NOTE: **single quotes (`'` ... `'`) and double quotes (`"` ... `"`) prevent the separation by a space of the individual values in the array.**

```bash
#!/bin/bash
domains=("www.inlanefreight.com ftp.inlanefreight.com vpn.inlanefreight.com" www2.inlanefreight.com)

echo ${domains[0]}
```
This will result in:
```bash
sosoBoy@htb[/htb]$ ./Arrays.sh

www.inlanefreight.com ftp.inlanefreight.com vpn.inlanefreight.com
```
