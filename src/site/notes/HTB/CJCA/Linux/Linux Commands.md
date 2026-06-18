---
{"dg-publish":true,"permalink":"/htb/cjca/linux/linux-commands/","dg-note-properties":{}}
---

## mkdir

mkdir command for each one would be time-consuming. Fortunately, the mkdir command has the -p (parents) option, which allows you to create parent directories automatically.
```
sosoBoy@htb[/htb]$ mkdir -p Storage/local/user/documents
```
==The command *tree .* shows the structure of the directory. The single dot (`.`) to indicate that you want to start from the current directory== 

One such important file is the  `/etc/passwd`  file. This file contains essential information about the users on the system, such as their usernames, user IDs (`UIDs`), group IDs (`GIDs`), and home directories.

Historically, the  `/etc/passwd`  file also stored password hashes, but now those hashes are typically stored in  `/etc/shadow`, which has stricter permissions. However, if the permissions on  `/etc/passwd`  or other critical files are not set correctly, it may expose sensitive information or lead to privilege escalation opportunities.

## which
this tool returns the path to the file or link that should be executed.
This allows us to determine if specific programs, like * cURL, netcat, wget, python, gcc,* are available on the operating system.

## find 
This is a useful tool to find files in the system. It allows multiple flags:
`sosoBoy@htb[/htb]$ find <location> <options>` 

###### examples of options:

| Option            | what it does        |
| ----------------- | ------------------- |
| `-type f`         | Specifies file type |
| `-name hello.txt` | specifies name      |
| `-size 20c`       | specifies bytes     |

==example of what such a command:==
`sosoBoy@htb[/htb]$ find / -type f -name *.conf -user root -size +20k -newermt 2020-03-03 -exec ls -al {} \; 2>/dev/null`

==Explanation==
`-type f` Hereby, we define the type of the searched object. In this case, '`f`' stands for '`file`'.

`-name *.conf` With '`-name`', we indicate the name of the file we are looking for. The asterisk (`*`) stands for 'all' files with the '`.conf`' extension.

`-user root`This option filters all files whose owner is the root user.

`-size +20k`We can then filter all the located files and specify that we only want to see the files that are larger than 20 KiB.

`-newermt 2020-03-03`With this option, we set the date. Only files newer than the specified date will be presented.

`-exec ls -al {} \;`This option executes the specified command, using the curly brackets as placeholders for each result. The backslash escapes the next character from being interpreted by the shell because otherwise, the semicolon would terminate the command and not reach the redirection.

`2>/dev/null`This is a  `STDERR`  redirection to the '`null device`', which we will come back to in the next section. This redirection ensures that no errors are displayed in the terminal. This redirection must  `not`  be an option of the 'find' command.


### Common tricks:
- When a file is dashed or has spaces in the filename: use quotes `'fileName'` or source `./-fileName`
- 