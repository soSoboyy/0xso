---
{"dg-publish":true,"permalink":"/0x/htb/cjca/networking/overview/","created":"2026-03-30T06:18:10.665+01:00","dg-note-properties":{}}
---

##### We can imagine `networking` as the delivery of mail or packages sent by one computer and received by the other.
A network enables two computers to communicate with each other. There is a wide array of :
- `topologies` (mesh/tree/star), 
- `mediums` (ethernet/fiber/coax/wireless), and
- `protocols` (TCP/UDP/IPX) that can be used to facilitate the network.

###### Examples:
- ACL can be seen as fence around a house. They are a protective layer and creates specific *entry* and *exit* points. Someone can jump over but that would be a suspicious activity.
- Map out the network purpose can be seen as placing light bulbs at each position for better visibility
- Having bushes around windows is a deterrent to people attempting to open the window. Just like *Intrusion Detection Systems* like Suricata or Snort are a deterrent to running network scans.
- Our post office is our `router` which we utilize to connect to the "`Internet`" in networking.
	- ==As soon as we send our packet through our post office (`router`), the packet is forwarded to the `main post office` (`ISP`). This main post office looks in the `address register`/`phonebook` (`Domain Name Service`) where this address is located and returns the corresponding geographical coordinates (`IP address`). Now that we know the address's exact location, our packet is sent directly there by a direct flight via our main post office.==
![Attachments/Pasted image 20260330051513.png](/img/user/0x/HTB/CJCA/Networking/Attachments/Pasted%20image%2020260330051513.png)
1. The Web Server should be in a DMZ (Demilitarized Zone) because clients on the internet can initiate communications with the website, making it more likely to become compromised. Placing it in a separate network allows the administrators to put networking protections between the web server and other devices.
2. Workstations should be on their own network.<mark style="background: #BBFABBA6;"> If a Workstation is on the same network as a Server, networking attacks like `spoofing` or `man in the middle` become much more of an issue.</mark>
3. The Switch and Router should be on an "Administration Network." This prevents workstations from snooping in on any communication between these devices. <mark style="background: #D2B3FFA6;">Since the router did not have a `trusted network`, anyone on the internal network could have sent a malicious advertisement and performed a `man in the middle` attack against any network.</mark>
4. IP Phones should be on their own network.  Placing them on their own network can allow network administrators to prioritize their traffic to prevent high latency more easily.
5. Printers should be on their own network. <mark style="background: #ADCCFFA6;">This may sound weird, but it is next to impossible to secure a printer. Due to how Windows works, if a printer tells a computer authentication is required during a print job, that computer will attempt an `NTLMv2` authentication, which can lead to passwords being stolen. Additionally, these devices are great for persistence and, in general, have tons of sensitive information sent to them.</mark>
