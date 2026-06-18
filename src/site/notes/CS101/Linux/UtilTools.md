---
{"dg-publish":true,"permalink":"/cs-101/linux/util-tools/","dg-note-properties":{}}
---

##### tee
#tee
When using `tee`, we transfer the received output and use the pipe (`|`) to forward it to `tee`. 
The most basic usage of the `tee` command is to display the standard output (`stdout`) of a program and write it to a file.

==Example==:
#diskfree
we are using the `df`  get information about the amount of available disk space on the file system. The output is piped to the `tee`command, which displays the output to the terminal and writes the same information to the file `disk_usage.txt`.

```shell

➜  ~ df -h | tee usage.txt

Filesystem       Size   Used  Avail Capacity iused     ifree %iused  Mounted on
/dev/disk1s5s1  233Gi   14Gi   48Gi    24%  502388 504039040    0%   /
devfs           337Ki  337Ki    0Bi   100%    1164         0  100%   /dev
/dev/disk1s4    233Gi  4.0Gi   48Gi     8%       5 504039040    0%   /System/Volumes/VM
/dev/disk1s2    233Gi  433Mi   48Gi     1%    2701 504039040    0%   /System/Volumes/Preboot
/dev/disk1s6    233Gi  6.2Mi   48Gi     1%      18 504039040    0%   /System/Volumes/Update
/dev/disk1s1    233Gi  165Gi   48Gi    78% 3441348 504039040    1%   /System/Volumes/Data
map auto_home     0Bi    0Bi    0Bi   100%       0         0  100%   /System/Volumes/Data/home
```

Here is another simple example that saves kernel messages while still showing them on screen:
```bash
dmesg | tee /tmp/dmesg.log
```


---
##### awk
#awk 
Awk is a text-processing language for extracting columns, filtering records, and reshaping structured data on the command line. It is built into every Linux and Unix system and handles tasks ranging from one-line column extraction to multi-stage data analysis.


---
##### ping
#ping
Ping works by sending one or more ICMP (Internet Control Message Protocol) Echo Request packets to a specified destination IP on the network and waiting for a reply. When the destination receives the packet, it responds with an ICMP echo reply. Check [icmp](HTB/CJCA/Protocols/ICMP)
```bash
ping -c 1 "ip address"
```
