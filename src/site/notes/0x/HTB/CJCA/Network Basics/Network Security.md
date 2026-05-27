---
{"dg-publish":true,"permalink":"/0x/htb/cjca/network-basics/network-security/","created":"2026-03-27T20:31:00.219+00:00","dg-note-properties":{}}
---

###### Some critical components of network security:
- *Firewalls and Intrusion Detection/Prevention Systems (IDS/IPS).*

==Firewall is a network security device, either hardware, software, or a combination of both, that monitors incoming and outgoing network traffic.== Firewalls enforce a set of rules (known as `firewall policies` or `access control lists`) to determine whether to `allow` or `block` specific traffic.

==Firewalls operate by analyzing packets of data according to predefined rules and policies, commonly focusing on factors such as IP addresses, port numbers, and protocols. This process, known as traffic filtering.==

#### 1. Packet Filtering Firewall

| **Description**                                                                                                 |
| --------------------------------------------------------------------------------------------------------------- |
| Operates at Layer 3 (Network) and Layer 4 (Transport) of the OSI model.                                         |
| Examines source/destination IP, source/destination port, and protocol type.                                     |
| `Example`: A simple router ACL that only allows HTTP (port 80) and HTTPS (port 443) while blocking other ports. |
#### 2. Stateful Inspection Firewall
<mark style="background: #ABF7F7A6;">Tracks the state of network connections.
`Example`: Only allows inbound data that matches an already established outbound request.
</mark>

#### 3. Application Layer Firewall (Proxy Firewall)
|                                                                                                 |
| ----------------------------------------------------------------------------------------------- |
| Operates up to Layer 7 (Application) of the OSI model.                                          |
| Can inspect the actual content of traffic (e.g., HTTP requests) and block malicious requests.   |
| `Example`: A web proxy that filters out malicious HTTP requests containing suspicious patterns. |
|                                                                                                 |

#### 4. Next-Generation Firewall (NGFW)
<mark style="background: #FFF3A3A6;">Combines stateful inspection with advanced features like deep packet inspection, intrusion detection/prevention, and application control.</mark>

#### Intrusion Detection and Prevention Systems (IDS/IPS)
Intrusion Detection and Prevention Systems (IDS/IPS) are security solutions designed to monitor and respond to suspicious network or system activity:
- IDS detects and alerts, does not block the suspicious traffic
- IPS detects and rejects malicious traffic in real time

==Both IDS and IPS solutions analyze network packets and compare them to known attack signatures or typical traffic patterns:==

- Signature based detection : Matches traffic against a database of known exploits.
- Anomaly based detection : Detects unusual activities
![[Attachments/Screenshot_2026-03-27_20-26-42.png \| 80]]
###### Type of IDS/IPS:
- <mark style="background: #CACFD9A6;">Network based: </mark> hardware or software place in the network:
	- `Example`: A sensor connected to the core switch that monitors traffic within a data center.

- <mark style="background: #D2B3FFA6;">Host-based: </mark>Runs on individual hosts or devices, monitoring inbound/outbound traffic:
	- `Example`: An antivirus or endpoint security agent installed on a server.

## Best Practices

| **Practice**                   | **Description**                                                                                                                                                                                                      |
| ------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Define Clear Policies`        | Consistent firewall rules based on the principle of `least privilege` (only allow what is necessary).                                                                                                                |
| `Regular Updates`              | Keep firewall, IDS/IPS signatures, and operating systems up to date to defend against the latest threats.                                                                                                            |
| `Monitor and Log Events`       | Regularly review firewall logs, IDS/IPS alerts, and system logs to identify suspicious patterns early.                                                                                                               |
| `Layered Security`             | Use `defense in depth` (a strategy that leverages multiple security measures to slow down an attack) with multiple layers: Firewalls, IDS/IPS, antivirus, and endpoint protection to cover different attack vectors. |
| `Periodic Penetration Testing` | Test the effectiveness of the security policies and devices by simulating real attacks.                                                                                                                              |
