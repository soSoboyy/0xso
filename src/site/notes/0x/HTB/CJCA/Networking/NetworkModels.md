---
{"dg-publish":true,"permalink":"/0x/htb/cjca/networking/network-models/","created":"2026-04-01T21:10:13.985+01:00","dg-note-properties":{}}
---

- The `OSI` model uses `seven` different layers, which are hierarchically based on each other to achieve this goal.
- The `TCP/IP` model is also a layered reference model, often referred to as the `Internet Protocol Suite`.
- 

![Attachments/Pasted image 20260401195108.png](/img/user/0x/HTB/CJCA/Networking/Attachments/Pasted%20image%2020260401195108.png)
In a layered system, devices in a layer exchange data in a different format called a `protocol data unit` (PDU).
==When an application sends a packet to the other system, the system works the layers shown above from layer `7` down to layer `1`, and the receiving system unpacks the received packet from layer `1` up to layer `7`.==

During the transmission, each layer adds a `header` to the `PDU` from the upper layer, which controls and identifies the packet. <mark style="background: #ADCCFFA6;">This process is called *encapsulation*</mark>. The header and the data together form the PDU for the next layer. The process continues to the `Physical Layer` or `Network Layer`, where the data is transmitted to the receiver. The receiver reverses the process and unpacks the data on each layer with the header information. 
![Attachments/Pasted image 20260401200417.png](/img/user/0x/HTB/CJCA/Networking/Attachments/Pasted%20image%2020260401200417.png)

*It is useful to understand and familiarize with both reference models.*
