---
{"dg-publish":true,"permalink":"/htb/cjca/bash/intro-bash/","dg-note-properties":{}}
---

#bash #ysap
The main difference between scripting and programming languages is that we don't need to compile the code to execute the scripting language, as opposed to programming languages.

Like a programming language, a scripting language has almost the same structure, which can be divided into:

- `Input` & `Output`
- `Arguments`, `Variables` & `Arrays`
- `Conditional execution`
- `Arithmetic`
- `Loops`
- `Comparison operators`
- `Functions`

In general, a script does not create a process, but it is executed by the interpreter that executes the script, in this case, the `Bash`.

Execute a script in bash
`bash hello.sh`
or
```bash
sh script.sh
# or
./hello.sh
```

## Shell
REPL = Read, Evaluate, Print, Loop this is what BASH does.
```bash
$ echo hello
hello
```

*Where does BASH live?* Bash process lives in the binary folder
```bash
$ which bash     
/usr/bin/bash
```

---
###### Navigation and Manipulation command
```bash
$ mkdir Bash
$ cd Bash
```
Create new files:
```bash
touch lesson-1.txt
touch lesson-2.txt
touch lesson-22.txt
```
We have a file with the typo? rename
```bash
mv lesson-22.txt lesson-3.txt
```
*Remove* all files: 
```bash
rm lesson-*.txt
```
The `*` is  a GLOB , called wildcard.

---
Find Terminal history
```bash
history 
```
![Attachments/Pasted image 20260511181446.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260511181446.png)
Give all the ran commands in Terminal

---
Make a hidden file
```bash
touch .file.txt
```
![Attachments/Pasted image 20260511181708.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260511181708.png)
Completely hidden

Show all the files:
```bash
ls -a
```
![Attachments/Pasted image 20260511182005.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260511182005.png)

---
###### Searching and Paging
The most used command is `grep`.
==It is a command to search for a **pattern** defined in the command.==

Example: Find all the words in the system's dictionary
```bash
#!/bin/bash
cat usr/share/dict/words
```
Which will give a list of words from A-Z , like this:
![Attachments/Pasted image 20260514172102.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514172102.png)

Now , to find something with `carl`  pattern:
```bash
#!/bin/bash
grep carl usr/share/dict/words
# or
grep 'carl' usr/share/dict/words
```
found this:
![Attachments/Pasted image 20260514172330.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514172330.png)

Or use **special characters** like : <mark style="background: #BBFABBA6;">`^` to find words that starts with that `sad` pattern</mark>:
```bash
#!/bin/bash
grep '^sad' /usr/share/dict/words
```
![Attachments/Pasted image 20260514172532.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514172532.png)

<mark style="background: #BBFABBA6;">`$` at the end to find words that end with that `er` pattern</mark>
```bash
#!/bin/bash
grep 'er
which gives:
![Attachments/Pasted image 20260514175751.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514175751.png)

---
###### Built-in commands vs external commands
Check the type of command:
```bash
type echo
```

`type` very useful command to check if command is built-in in shell or a binary:
┌──(kali[~]
└─$ type ls      
ls is an alias for ls --color=auto

┌──(kali[~]
└─$ type cd
cd is a shell builtin


 /usr/share/dict/words
```
which gives:
![Attachments/Pasted image 20260514175751.png](/img/user/HTB/CJCA/Bash/Attachments/Pasted%20image%2020260514175751.png)

---
###### Built-in commands vs external commands
Check the type of command:
{{CODE_BLOCK_14}}

`type` very useful command to check if command is built-in in shell or a binary:
┌──(kali[~]
└─$ type ls      
ls is an alias for ls --color=auto

┌──(kali[~]
└─$ type cd
cd is a shell builtin


