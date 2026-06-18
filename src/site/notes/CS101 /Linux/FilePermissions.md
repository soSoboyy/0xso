---
{"dg-publish":true,"permalink":"/cs-101/linux/file-permissions/","dg-note-properties":{}}
---

#permissions
# Linux file permissions

When typed `ls -l` , the shell provides a list of all the files. It shows something like this:
![attachments/Screenshot 2026-03-14 at 16.58.42.png](/img/user/CS101%20/Linux/attachments/Screenshot%202026-03-14%20at%2016.58.42.png)

- File type: `-` for *files* or `d` for *directories* 
- Permission settings: `rw-r--r--` *root, user , group*
	- The first set of permissions applies to the owner of the file.
	- The second set of permissions applies to the user group that owns the file. 
	- The third set of permissions is generally referred to as "others."

#### *When permissions and users are represented by letters, that is called **symbolic mode**. For users, `u` stands for user owner, `g` for group owner, and `o` for others.

##### When Linux file permissions are represented by numbers, it's called numeric mode.
###### In numeric mode, a three-digit value represents specific file permissions (for example, 744.) These are called **octal values**. The first digit is for owner permissions, the second for group permissions, and the third for other users.

| Symbolic mode                        | Numeric mode                                        |
| ------------------------------------ | --------------------------------------------------- |
| `r` Read<br>`w` Write<br>`x` Execute | - r (read): 4<br>- w (write): 2<br>- x (execute): 1 |
|                                      |                                                     |

# Essential Keywords

| systemctl    | System control gives control over the system, such:<br>- enable, disable<br>- Start, stop | Example:                                                                                                                                                      |
| ------------ | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| frewall-cmd  | Firewall command                                                                          |                                                                                                                                                               |
| ss / netstat | Socket status /  Network status                                                           | `ss -l` Show only listening port<br>`ss -tul` Show only socket listening for TCP, UDP<br>`ss -tulp` Show only socket listening for TCP, UDP and which process |
