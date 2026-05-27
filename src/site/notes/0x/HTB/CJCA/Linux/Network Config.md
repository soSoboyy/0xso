---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/network-config/","created":"2026-05-04T10:55:28.419+01:00","dg-note-properties":{}}
---

*As a penetration tester, one of the essential skills is configuring and managing network settings on Linux systems.*
One of the primary tasks in network configuration is managing network interfaces.

#####  Network Access Control
Another vital component of network configuration is network access control (`NAC`). *As penetration testers, we need to be well-versed in how NAC can enhance network security and the various technologies available. * Key NAC models include:

| **Type**                             | **Description**                                                                                                           |
| ------------------------------------ | ------------------------------------------------------------------------------------------------------------------------- |
| Discretionary Access Control (`DAC`) | This model allows the owner of the resource to set permissions for who can access it.                                     |
| Mandatory Access Control (`MAC`)     | Permissions are enforced by the operating system, not the owner of the resource, making it more secure but less flexible. |
| Role-Based Access Control (`RBAC`)   | Permissions are assigned based on roles within an organization, making it easier to manage user privileges.               |
Security NAC policies:
- SELinux (Security-Enhanced Linux)
- AppArmor (profiles for application security)
- TCP wrappers (access based on IP)

---
## Configuring Network Interfaces

To list all the network interfaces we use the `ifconfig` or `ip` commands.
###### Activate Network Interface:
```shell
sudo ifconfig eth0 up #standard
#or
sudo ip link set eth0 up
``` 

######  Assign IP Address to an Interface
```shell
sudo ifconfig eth0 192.168.1.2
```

###### Set netmask
```shell
sudo ifconfig eth0 netmask 255.255.255.0
```

==Ensuring that the default gateway is set correctly is important, as incorrect configuration can lead to connectivity issues, we can use the `route` command with the `add` option.==
###### Assign the Route to an Interface
```shell
sudo route add default gw 192.168.1.1 eth0
```

 <mark style="background: #FF5582A6;">NOTE: </mark>
 Proper DNS configuration is crucial for enabling devices to access websites, online services, and other networked resources. Without correctly configured DNS servers, devices may experience issues such as the inability to resolve domain names, leading to network connectivity problems.
 
 *On Linux systems,* this can be achieved by updating the `/etc/resolv.conf` file, which is a simple text file containing the system’s DNS information. By adding the appropriate DNS server addresses (Google's public DNS - `8.8.8.8` or `8.8.4.4`), the system can correctly resolve domain names to IP addresses, ensuring smooth communication over the network.

###### Edit DNS settings:
```shell
sudo vim /etc/resolv.conf
```

 /etc/resolv.conf

```txt
nameserver 8.8.8.8
nameserver 8.8.4.4
```

<mark style="background: #BBFABBA6;">*It’s important to note* that changes made directly to the `/etc/resolv.conf` file are not persistent across reboots or network configuration changes. This is because the file may be automatically overwritten by network management services like `NetworkManager` or `systemd-resolved`.</mark>

###### Editing Interfaces
`sudo vim /etc/network/interfaces`

This will open the `interfaces` file in the vim editor. We can add the network configuration settings to the file like this:
```txt
auto eth0
iface eth0 inet static 
  address 192.168.1.2  
  netmask 255.255.255.0 
  gateway 192.168.1.1  
  dns-nameservers 8.8.8.8 8.8.4.4
```

###### Restart Networking Service
```shell
sudo systemctl restart networking
```
