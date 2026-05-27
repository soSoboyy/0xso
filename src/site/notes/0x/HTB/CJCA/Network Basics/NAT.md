---
{"dg-publish":true,"permalink":"/0x/htb/cjca/network-basics/nat/","created":"2026-03-27T06:22:04.690+00:00","dg-note-properties":{}}
---

## Network Address Translation:
NAT allows multiple devices on a private network to share a single public IP address. This not only helps conserve the limited pool of public IP addresses but also adds a layer of security to the internal network.

*Public IP addresses are globally unique identifiers assigned by Internet Service Providers (ISPs)*

*Private IP addresses are designated for use within local networks. These addresses are not routable on the global internet, meaning packets sent to these addresses are not forwarded by internet.*
![Attachments/Pasted image 20260327060932.png](/img/user/0x/HTB/CJCA/Network%20Basics/Attachments/Pasted%20image%2020260327060932.png)

Network Address Translation (NAT) is a process carried out by a router that modifies the source or destination IP address in the headers of IP packets as they pass through. This modification is used to translate the private IP into the public IP of the router.

![Attachments/NAT.jpg](/img/user/0x/HTB/CJCA/Network%20Basics/Attachments/NAT.jpg)
<mark style="background: #FFF3A3A6;">3 types of NAT :</mark>

| Static                                                                                                    | Dynamic                                                                                                    | PAT(Port Address Translation)                                                                                                                                                                                                                                                                                                                           |
| --------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Involves a one-to-one mapping, where each private IP address corresponds directly to a public IP address. | Assigns a public IP from a pool of available addresses to a private IP as needed, based on network demand. | Also known as NAT Overload, is the most common form of NAT in home networks. Multiple private IP addresses share a single public IP address, differentiating connections by using unique port numbers. This method is widely used in home and small office networks, allowing multiple devices to share a single public IP address for internet access. |
