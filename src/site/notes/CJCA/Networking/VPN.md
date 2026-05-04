---
{"dg-publish":true,"permalink":"/cjca/networking/vpn/","created":"2026-04-04T14:20:17.833+01:00","dg-note-properties":{}}
---

A `Virtual Private Network` (`VPN`) is a technology that allows a secure and encrypted connection between a private network and a remote device.
<mark style="background: #ABF7F7A6;">- This allows the remote machine to access the private network directly, providing secure and confidential access to the network's resources and services.</mark>
<mark style="background: #FFF3A3A6;">- Another reason is that VPNs allow employees to access the private network and its resources remotely from anywhere, as long as they have an internet connection.</mark>

VPN typically uses the ports `TCP/1723` for [Point-to-Point Tunneling Protocol `PPTP` VPN connections.
<mark style="background: #FF5582A6;">(This protocol is not considered secure anymore)</mark>
At the TCP/IP layer, a VPN connection typically uses the Encapsulating Security Payload (`ESP`) protocol to encrypt and authenticate the VPN traffic.

#ipsec

## IPsec: Internet Protocol Security:
It is a powerful and widely-used security protocol that provides encryption and authentication for internet communications and works by encrypting the data payload of each IP packet and adding an `authentication header` (`AH`), which is used to verify the integrity and authenticity of the packet.

IPsec uses a combination of two protocols to provide encryption and authentication:
- `AH` - <mark style="background: #FFB86CA6;">This protocol provides integrity and authenticity for IP packets but does not provide encryption. </mark> It adds an authentication header to each IP packet, which contains a cryptographic checksum that can be used to verify that the packet has not been tampered with.
- `Encapsulating Security Payload (ESP)`: This protocol provides encryption and optional authentication for IP packets.

<mark style="background: #FF5582A6;">IPsec can be used in two modes.</mark>

|**Mode**|**Description**|
|---|---|
|`Transport Mode`|In this mode, IPsec encrypts and authenticates the data payload of each IP packet but does not encrypt the IP header. This is typically used to secure end-to-end communication between two hosts.|
|`Tunnel Mode`|With this mode, IPsec encrypts and authenticates the entire IP packet, including the IP header. This is typically used to create a VPN tunnel between two networks.|
