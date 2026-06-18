---
{"dg-publish":true,"permalink":"/htb/cjca/config-files/","dg-note-properties":{}}
---

#configfiles #configuration
## network services
#services
<mark style="background: #FF5582A6;">Apache PORT config file</mark> : `/etc/apache2/ports.conf`

<mark style="background: #FF5582A6;">Apache config file</mark> : `/etc/apache2/apache2.conf`

<mark style="background: #FFB8EBA6;">SSH daemon file can be configured in</mark>  : `/etc/ssh/sshd_config` 

<mark style="background: #FFB86CA6;">NFS </mark>: `/etc/exports`

<mark style="background: #FFF3A3A6;">OpenVPN</mark> : `/etc/openvpn/server.conf`

<mark style="background: #D2B3FFA6;">DNS information</mark> : `/etc/resolv.conf`

<mark style="background: #ADCCFFA6;">Network Interface</mark> : `/etc/network/interfaces`

<mark style="background: #ABF7F7A6;">TCP wrappers </mark>use the following configuration files:

- `/etc/hosts.allow`
- `/etc/hosts.deny`

--- 
## File systems
#filesystem
<mark style="background: #CACFD9A6;">file system mounting</mark> : `/etc/fstab`

---
## Logs
#logs
- Kernel Logs : `/var/log/kern.log`
- System Logs : `/var/log/syslog`
- Authentication Logs : `/var/log/auth.log` 
- Application Logs : 
- Security Logs : 