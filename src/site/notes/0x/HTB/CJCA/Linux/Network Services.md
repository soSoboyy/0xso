---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/network-services/","created":"2026-04-18T06:37:17.344+01:00","dg-note-properties":{}}
---


# Network Services 
Learning Linux network services are essential to master Linux proficiency.
*Network services are designed to perform specific tasks, many of which enable remote operations.*
They allow:
- Establish connections
- transfer files
- analyse network traffic
- configure service files

## SSH
Is a network protocol that allows the secure transmission of data and commands over a network.
*To connect to a remote Linux host via SSH, a corresponding SSH server (OpenSSH server ) must be available and running.* 

###### Install server
`sosoBoy@htb[/htb]$ sudo apt install openssh-server -y`

###### Status server
`sosoBoy@htb[/htb]$ systemctl status ssh`

###### Where to find the SSH file? 
The SSH daemon file can be configured in `/etc/ssh/sshd_config` with Vim.

## NFS
Network File System (`NFS`) is a network protocol that allows us to store and manage files on remote systems as if they were stored on the local system.
(We can use this service just like FTP in case there is no FTP client installed on the target system, or NFS is running instead of FTP.)

We can configure NFS via the configuration file `/etc/exports`
*This file specifies which directories should be shared and the access rights for users and systems*

Here are some important access rights that can be configured in NFS:

**Permissions**

| **Permissions**  | **Description**                                                                                                                                            |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `rw`             | Gives users and systems read and write permissions to the shared directory.                                                                                |
| `ro`             | Gives users and systems read-only access to the shared directory.                                                                                          |
| `no_root_squash` | Prevents the root user on the client from being restricted to the rights of a normal user.                                                                 |
| `root_squash`    | Restricts the rights of the root user on the client to the rights of a normal user.                                                                        |
| `sync`           | Synchronizes the transfer of data to ensure that changes are only transferred after they have been saved on the file system.                               |
| `async`          | Transfers data asynchronously, which makes the transfer faster, but may cause inconsistencies in the file system if changes have not been fully committed. |

#### Create NFS Share
For example, we can create a new folder and share it temporarily in NFS. We would do this as follows:
```shell
cry0l1t3@htb:~$ mkdir nfs_sharing
cry0l1t3@htb:~$ echo '/home/cry0l1t3/nfs_sharing hostname(rw,sync,no_root_squash)' >> /etc/exports 
cry0l1t3@htb:~$ cat /etc/exports | grep -v "#"   

/home/cry0l1t3/nfs_sharing hostname(rw,sync,no_root_squash)
```

If we have created an NFS share and want to work with it on the target system, *we have to mount it first.* We can do this with the following command:
#### Mount NFS Share

```bash
cry0l1t3@htb:~$ mkdir ~/target_nfs 
cry0l1t3@htb:~$ mount 10.129.12.17:/home/john/dev_scripts ~/target_nfs cry0l1t3@htb:~$ tree ~/target_nfs 

target_nfs/ 
├── css.css 
├── html.html 
├── javascript.js 
├── php.php 
└── xml.xml 
0 directories, 5 files`
```
So we have mounted the NFS share (`dev_scripts`) from our target (`10.129.12.17`) locally to our system in the mount point `target_nfs` over the network and can view the contents just as if we were on the target system. There are even some methods that can be used in specific cases to escalate our privileges on the remote system using NFS.

## Web Servers:
A web server is software that delivers data, documents, applications, and various functions over the Internet. It uses *HTTP* , an application layer protocol to send and receive data. It data then is rendered in HTML within the client's browser, facilitating the creation of dynamic web pages that respond interactively to user request.
The most widely used web servers on Linux platforms are :
- Apache, Nginx, Lighttpd, and Caddy
with Apache being particularly popular due to its broad compatibility with operating systems including Ubuntu, Solaris, and Red Hat Linux.

==Additionally, web servers can be leveraged to conduct phishing attacks by hosting replicas of target pages, thereby attempting to capture user credentials.==

#### Install Apache Web Server:

`sosoBoy@htb[/htb]$ sudo apt install apache2 -y`
For Apache2, to specify which folders can be accessed, we can edit the file `/etc/apache2/apache2.conf` with a text editor. 
*This file contains the global settings. We can change the settings to specify which directories can be accessed and what actions can be performed on those directories.*
#### Apache Configuration

<Directory /var/www/html>
	Options Indexes FollowSymLinks        
	AllowOverride All        
	Require all granted 
</directory>`

==This section specifies that the default `/var/www/html` folder is accessible, that users can use the `Indexes` and `FollowSymLinks` options, that changes to files in this directory can be overridden with `AllowOverride All`, and that `Require all granted` grants all users access to this directory. For example, if we want to transfer files to one of our target systems using a web server, we can put the appropriate files in the `/var/www/html` folder and use `wget` or `curl` or other applications to download these files on the target system.==

It is also possible to customize individual settings at the directory level by using the `.htaccess` file, which we can create in the directory in question. This file allows us to configure certain directory-level settings, such as access controls, without having to customize the Apache configuration file. We can also add modules to get features like `mod_rewrite`, `mod_security`, and `mod_ssl` that help us improve the security of our web application. ==

#### Python Webserver
Python Web Server is a simple, fast alternative to Apache and can be used to host a single folder with a single command to transfer files to another system.

###### How to install and run a Python Webser:

`sosoBoy@htb[/htb]$ sudo apt install python3 -y`

`sosoBoy@htb[/htb]$ python3 -m http.server`

The second command will run a Python Webserver in the TCP/8000 port.
*To host another folder in the directory* : 
```shell
sosoBoy@htb[/htb]$ python3 -m http.server --directory /home/cry0l1t3/target_files
```
This will start a Python web server on the `TCP/8000` port, and we can access the `/home/cry0l1t3/target_files` folder from the browser

If we want to lunch the webserver in a different port :
`sosoBoy@htb[/htb]$ python3 -m http.server 443` 

## OpenVPN
For penetration testers, OpenVPN offers invaluable capabilities. It allows testers to securely connect to internal networks, especially when direct access is not feasible due to geographical constraints.

#### Install OpenVPN

`sosoBoy@htb[/htb]$ sudo apt install openvpn -y` 

OpenVPN can be customized and configured by editing the configuration file  `/etc/openvpn/server.conf`. This file contains the settings for the OpenVPN server.
If we want to connect to an OpenVPN server, we can use the  `.ovpn`  file we received from the server and save it on our system. We can do this with the following command on the command line:

#### Connect to VPN
`sosoBoy@htb[/htb]$ sudo openvpn --config internal.ovpn` 
After the connection is established, we can communicate with the internal hosts on the internal network.



