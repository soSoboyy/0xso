---
{"dg-publish":true,"permalink":"/htb/cjca/protocols/arp/","dg-note-properties":{}}
---

Address Resolution Protocol is a network protocol.
<mark style="background: #BBFABBA6;">It is an important part of the network communication used to resolve a network layer (layer 3) IP address to a link layer (layer 2) MAC address. It maps a host's IP address to its corresponding MAC address to facilitate communication between devices on a LAN.</mark>

When a device on a LAN wants to communicate with another device, *it sends a broadcast message containing the destination IP address and its own MAC address.* The device with the matching IP address responds with its own MAC address, and the two devices can then communicate directly using their MAC addresses. *This process is known as ARP resolution.*
![[Attachments/660e83b14df965cb2d2a4210_uHpUWkHG-QfPRO5WecXPTaOmIBohmaTIy9qlqYE16gCqxmkoeSKmgRN_lfW2bR5vIO5FU9Mz_lx4PSbNY7gbkWeQBItJq-bPjhZhT9pF1_BV-wAi8EjobsnN5kHZGBsN-b0VIEwE.webp \| 400]]
ARP allows devices to send and receive data using MAC addresses rather than IP addresses
#### 2 type of messages:
- <mark style="background: #FFB8EBA6;">Request</mark>: ARP request to resolve the destination device's IP address to its MAC address. The request is broadcast to all devices on the LAN and contains the IP address of the destination device.
- <mark style="background: #FFB8EBA6;">Replay</mark>: Device replies and the message contains the IP and MAC addresses of both the requesting and the responding devices.
![Attachments/Pasted image 20260403105343.png](/img/user/HTB/CJCA/Protocols/Attachments/Pasted%20image%2020260403105343.png)

