---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/permissions-and-management/","created":"2026-04-12T13:34:33.116+01:00","dg-note-properties":{}}
---

Check my Linux [notes here](obsidian://open?vault=0xsoso&file=CS101%2FLinux%2FFilePermissions)

###### Linux permissions act like a set of rules or keys that dictate who can access or modify certain resources, ensuring security and proper collaboration across the system.

When a user wants to access the contents of a Linux directory, it's similar to unlocking a door before stepping inside. <mark style="background: #FF5582A6;">To "traverse" or navigate into a directory, the user must first have the right key—this key is the `execute` permission on the directory.</mark>

The permissions can be set for the `owner`, `group`, and `others` like presented in the next example with their corresponding permissions.

## Change Permissions

We can modify permissions using the `chmod` command, permission group references (`u` - owner, `g` - Group, `o` - others, `a` - All users), and either a `+` or a `-` to add or remove the designated permissions.
```shell
cry0l1t3@htb[/htb]$ chmod a+r shell && ls -l shell -rwxr-xr-x 1 cry0l1t3 htbteam 0 May 4 22:12 shell
```

## Change Owner

To change the owner and/or the group assignments of a file or directory, we can use the `chown` command. The syntax is like following:
#### Syntax - chown:

`cry0l1t3@htb[/htb]$ chown <user>:<group> <file/directory>`

In this example, "shell" can be replaced with any arbitrary file or folder.

`cry0l1t3@htb[/htb]$ chown root:root shell 

## Sticky Bit

Sticky bits in Linux are like locks on files within shared spaces. When set on a directory, the sticky bit adds an extra layer of security, ensuring that only certain individuals can modify or delete files, even if 

# User management
The `/etc/shadow` file is a critical system file that stores encrypted password information for all user accounts. For security reasons, it is readable and writable only by the root user to prevent unauthorized access to sensitive authentication data.
#### Execution as root:
To perform tasks that require elevated privileges, users can utilize the `sudo` command. 

#### Create new user:
`sudo userAdd -m 0x` : Where `-m` ensure a new home directory  is created
`su --command whoami  ` : When executing su as a different user, the flag `--command ` has to be specified with the command.


