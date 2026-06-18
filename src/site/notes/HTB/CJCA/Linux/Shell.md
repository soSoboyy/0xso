---
{"dg-publish":true,"permalink":"/htb/cjca/linux/shell/","dg-note-properties":{}}
---

*my notes from the 12-hour BASH course by YSAP [here](obsidian://open?vault=soSo&file=CS101%2FLinux%2FShell.canvas)*

==(These notes are from HTB)==

###### Unprivileged - User Shell Prompt `$`
###### Privileged - Root Shell Prompt `#`

##### PS variable:
The `PS1` variable in Linux systems controls how your command prompt looks in the terminal. By customizing the PS1 variable, it is possible to  change:
the prompt to display information such as your username, your computer's name, the current folder you're in, or even add colors and special characters.

shell prompts can be customized using special characters and variables in the shell’s configuration file (`.bashrc` for the Bash shell,==should be in the user's home dir==). For example, we can use: the `\u` character to represent the current username, `\h` for the hostname, and `\w` for the current working directory.

| **Special Character** | **Description**                            |
| --------------------- | ------------------------------------------ |
| `\d`                  | Date (Mon Feb 6)                           |
| `\D{%Y-%m-%d}`        | Date (YYYY-MM-DD)                          |
| `\H`                  | Full hostname                              |
| `\j`                  | Number of jobs managed by the shell        |
| `\n`                  | Newline                                    |
| `\r`                  | Carriage return                            |
| `\s`                  | Name of the shell                          |
| `\t`                  | Current time 24-hour (HH:MM:SS)            |
| `\T`                  | Current time 12-hour (HH:MM:SS)            |
| `\@`                  | Current time                               |
| `\u`                  | Current username                           |
| `\w`                  | Full path of the current working directory |
[explainshell](https://explainshell.com/)
## man
to discover which options a tool or command offers, the `man` command is the best option:
```
sosoBoy@htb[/htb]$ man ls
```
==we can also quickly look at the optional parameters without browsing through the complete documentation==
```
ls --help or ls -h
```

Another tool that can be useful in the beginning is `apropos` , which provides a shorter description for a given command.

## ls
`ls` command lists all the content inside a directory, but it has also additional options:

```
cry0l1t3@htb[~]$ ls -l

total 32
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:37 Desktop
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Documents
drwxr-xr-x 3 cry0l1t3 htbacademy 4096 Nov 15 03:26 Downloads
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Music
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Pictures
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Public
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Templates
drwxr-xr-x 2 cry0l1t3 htbacademy 4096 Nov 13 17:34 Videos
```
This shows : *file type (d) and permission(root, user, group)* , n.of hard links in the dir, owner, group owner, size of files, date, dir name,

==A directory can also have hidden files that start with a dot at the beginning of its name (e.g., `.bashrc` or `.bash_history`). Therefore, we need to use the command `ls -la` to `list all` files of a directory==

