---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/system-info/","created":"2026-04-05T18:22:47.307+01:00","dg-note-properties":{}}
---

==Below is a list of essential tools to help gather information about system details, processes, network configurations, users/user settings, and directories, along with their related parameters.==


<mark style="background: #FFB86CA6;">Sudo rights could help us escalate privileges or could be a sign to a sysadmin that they may need to audit permissions and group memberships to remove any access that is not required for a given user to carry out their day-to-day tasks.</mark>

|**Command**|**Description**|
|---|---|
|`whoami`|Displays current username.|
|`id`|Returns users identity|
|`hostname`|Sets or prints the name of current host system.|
|`uname`|Prints basic information about the operating system name and system hardware.|
|`pwd`|Returns working directory name.|
|`ifconfig`|The ifconfig utility is used to assign or to view an address to a network interface and/or configure network interface parameters.|
|`ip`|Ip is a utility to show or manipulate routing, network devices, interfaces and tunnels.|
|`netstat`|Shows network status.|
|`ss`|Another utility to investigate sockets.|
|`ps`|Shows process status.|
|`who`|Displays who is logged in.|
|`env`|Prints environment or sets and executes command.|
|`lsblk`|Lists block devices.|
|`lsusb`|Lists USB devices|
|`lsof`|Lists opened files.|
|`lspci`|Lists PCI devices.|

##### Uname
Running `uname -a` will print all information about the machine in a specific order: kernel name, hostname, the kernel release, kernel version, machine hardware name, and operating system. The `-a` flag will omit `-p` (processor type) and `-i` (hardware platform) if they are unknown.
The flag `-r` shows the kernel release.

##### ls
The `ls` command is used to list all content in a directory