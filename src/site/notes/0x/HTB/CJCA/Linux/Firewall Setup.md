---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/firewall-setup/","created":"2026-05-11T16:47:41.422+01:00","dg-note-properties":{}}
---

<mark style="background: #FF5582A6;">The primary goal of firewalls is to provide a security mechanism for controlling and monitoring network traffic between different network segments, such as internal and external networks or different network zones.</mark>

In Linux there is a built-in firewall system that can  be used to control the network traffic, *they can filter incoming and outgoing traffic based on pre-defined rules, protocols, ports, and other criteria to prevent unauthorized access.*

==In Linux, the firewall functionality is typically implemented using the Netfilter framework==, which is an integral part of the kernel. ==Netfilter provides a set of hooks that can be used to intercept and modify network traffic as it passes through the system.== The iptables utility is commonly used to configure the firewall rules on Linux systems.
#iptable
The iptables utility provides a flexible set of rules for filtering network traffic based on various criteria.
- `Nftables` provides a more modern syntax and improved performance over iptables. *However, the syntax of nftables rules is not compatible with iptables*
- `UFW` stands for “Uncomplicated Firewall” and provides a simple and user-friendly interface for configuring firewall rules. UFW is built on top of the iptables framework like nftables and provides an easier way to manage firewall rules.
- FirewallD provides a dynamic and flexible firewall solution that can be used to manage complex firewall configurations.

==The main components of iptables are:==

| **Component** | **Description**                                                                                                                                                                                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Tables`      | Tables are used to organize and categorize firewall rules.                                                                                                                                                                                                                         |
| `Chains`      | Chains are used to group a set of firewall rules applied to a specific type of network traffic. ==chains organize rules that define how network traffic should be filtered or modified.== There are two types of chains in iptables:<br>- Built-in chains<br>- User-defined chains |
| `Rules`       | Rules define the criteria for filtering network traffic and the actions to take for packets that match the criteria.                                                                                                                                                               |
| `Matches`     | Matches are used to match specific criteria for filtering network traffic, such as source or destination IP addresses, ports, protocols, and more.                                                                                                                                 |
| `Targets`     | Targets specify the action for packets that match a specific rule. For example, targets can be used to accept, drop, or reject packets or modify the packets in another way.                                                                                                       |
|               |                                                                                                                                                                                                                                                                                    |
#### Tables , Chains
When working with firewalls on Linux systems, it is important to understand how tables work in iptables. Tables in iptables are used to categorize and organize firewall rules based on the type:
*Each table is responsible for performing a specific set of tasks.*

| **Table Name**      | **Description**                                                             | **Built-in Chains**                             | ==The built-in chains are pre-defined and automatically created when a table is created.==                                                                                                                                                                       |
| ------------------- | --------------------------------------------------------------------------- | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `filter`            | Used to filter network traffic based on IP addresses, ports, and protocols. | INPUT, OUTPUT, FORWARD                          | These chains are used to filter incoming and outgoing network traffic, as well as traffic that is being forwarded between different network interfaces.                                                                                                          |
| `nat`               | Used to modify the source or destination IP addresses of network packets.   | PREROUTING, POSTROUTING                         | The PREROUTING chain is used to *modify the destination IP address* of incoming packets before the routing table processes them. The POSTROUTING chain is used to *modify the source IP address *of outgoing packets after the routing table has processed them. |
| `mangle`            | Used to modify the header fields of network packets.                        | PREROUTING, OUTPUT, INPUT, FORWARD, POSTROUTING | These chains are used to modify the header fields of incoming and outgoing packets and packets being processed by the corresponding chains.                                                                                                                      |
| User-defined chains | They can be added to any of the three main tables.                          |                                                 | For example, if an organization has multiple web servers that all require similar firewall rules, the rules for each server could be grouped in a user-defined chain.                                                                                            |
#### Rules and Targets
Iptables rules are used to define the criteria for filtering network traffic and the actions to take for packets that match the criteria.
*Rules are added to chains using the `-A` option followed by the chain name,* and they can be modified or deleted using various other options.

The criteria or matches match specific fields in the IP header, such as:
- IP address, 
- protocol, 
- source, 
- destination port number, and more
==For example, targets can accept, drop, reject, or modify the packets. Some of the common targets used in iptables rules include the following:==

|**Target Name**|**Description**|
|---|---|
|`ACCEPT`|Allows the packet to pass through the firewall and continue to its destination|
|`DROP`|Drops the packet, effectively blocking it from passing through the firewall|
|`REJECT`|Drops the packet and sends an error message back to the source address, notifying them that the packet was blocked|
|`LOG`|Logs the packet information to the system log|
|`SNAT`|Modifies the source IP address of the packet, typically used for Network Address Translation (NAT) to translate private IP addresses to public IP addresses|
|`DNAT`|Modifies the destination IP address of the packet, typically used for NAT to forward traffic from one IP address to another|
|`MASQUERADE`|Similar to SNAT but used when the source IP address is not fixed, such as in a dynamic IP address scenario|
|`REDIRECT`|Redirects packets to another port or IP address|
|`MARK`|Adds or modifies the Netfilter mark value of the packet, which can be used for advanced routing or other purposes|

Let us illustrate a rule and consider that we want to add a new entry to the INPUT chain that allows incoming TCP traffic on port 22 (SSH) to be accepted. The command for that would look like the following:
```bash
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
```

#### Matches

`Matches` are used to specify the criteria that determine whether a firewall rule should be applied to a particular packet or connection. Matches are used to match specific characteristics of network traffic, such as the source or destination IP address, protocol, port number, and more.

|**Match Name**|**Description**|
|---|---|
|`-p` or `--protocol`|Specifies the protocol to match (e.g. tcp, udp, icmp)|
|`--dport`|Specifies the destination port to match|
|`--sport`|Specifies the source port to match|
|`-s` or `--source`|Specifies the source IP address to match|
|`-d` or `--destination`|Specifies the destination IP address to match|
|`-m state`|Matches the state of a connection (e.g. NEW, ESTABLISHED, RELATED)|
|`-m multiport`|Matches multiple ports or port ranges|
|`-m tcp`|Matches TCP packets and includes additional TCP-specific options|
|`-m udp`|Matches UDP packets and includes additional UDP-specific options|
|`-m string`|Matches packets that contain a specific string|
|`-m limit`|Matches packets at a specified rate limit|
|`-m conntrack`|Matches packets based on their connection tracking information|
|`-m mark`|Matches packets based on their Netfilter mark value|
|`-m mac`|Matches packets based on their MAC address|
|`-m iprange`|Matches packets based on a range of IP addresses|

In general, *matches are specified using the `-m`option in iptables*. For example, the following command adds a rule to the 'INPUT' chain in the 'filter' table that matches incoming TCP traffic on port 80: 
```bash
sudo iptables -A INPUT -p tcp -m tcp --dport 80 -j ACCEPT
```

This example rule matches incoming TCP traffic (`-p tcp`) on port 80 (`--dport 80`) and jumps to the accept target (`-j ACCEPT`) if the match is successful.

###### This module has exercises at the end
