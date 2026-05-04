---
{"dg-publish":true,"permalink":"/cjca/networking/wireless/","created":"2026-04-03T12:25:21.447+01:00","dg-note-properties":{}}
---

<mark style="background: #FFF3A3A6;">Wireless networks use radio frequency (`RF`) technology to transmit data between devices.</mark> Each device on a wireless network has a wireless adapter that converts data into RF signals and sends them over the air.

For example, a local area network (LAN) that covers a small area, such as a home or small office, might use a wireless technology called `WiFi`, which has a range of a few hundred feet. On the other hand, a wireless wide area network (`WWAN`) might use mobile telecommunication technology such as cellular data (`3G`, `4G LTE`, `5G`)

When a device, like a laptop, wants to send data over the network, it first communicates with the [Wireless Access Point] to request permission to transmit.

## WiFi Connection
To connect to the router, the laptop uses a wireless networking protocol called IEEE 802.1.1 and authenticates with the Service Set Identifier (*SSID*) and password.
<mark style="background: #CACFD9A6;">When a device wants to join a WiFi network, it sends a request to the WAP to initiate the connection process.</mark> It sends a request called  <mark style="background: #BBFABBA6;">REQUEST FRAME</mark> and includes:
- MAC 
- SSID
- Data rate
- Channels
- Security protocol

The challenge-response handshake is a process to establish a secure connection between a WAP and a client device using the WEP (Wired Equivalent Privacy) security protocol.

####  WiFi networks have several security features to protect against unauthorized access and ensure the privacy and integrity of data transmitted over the network:
##### - Encryption:
	- WEP, WPA2, WPA3
- Access Control:
	- WiFi networks are configured by default to allow authorised devices to join the network using specific authentication methods.
		- ## Authentication Protocols:
		-  [Extensible Authentication Protocol] (`EAP`), a framework for authentication used in various networking contexts.
		- [Lightweight Extensible Authentication Protocol] (`LEAP`) and [Protected Extensible Authentication Protocol] (`PEAP`) are authentication protocols used to secure wireless networks and provide a secure method for authenticating devices on a wireless network, often used in conjunction with WEP or WPA to provide an additional layer of security.
			- - <mark style="background: #FF5582A6;">`LEAP` uses a `shared key` for authentication, which means that the `same key` is used for `encryption and authentication`.</mark>
			- <mark style="background: #BBFABBA6;">`PEAP` uses a more secure authentication method called tunneled [Transport Layer Security] (`TLS`). This method establishes a secure connection between the device and the WAP using a `digital certificate`, and an encrypted tunnel protects the authentication process.</mark>
			
- Firewall

## Disassociation Attack

A [Disassociation Attack] is a *type of `all` wireless network attack that aims to disrupt the communication between a WAP and its clients by sending disassociation frames to one or more clients.*

## Wireless Hardening
==There are many different ways to protect wireless networks:==
#### Disabling Broadcasting:
Disabling the broadcasting of the SSID is a security measure that can help harden a WAP by making it more difficult to discover and connect to the network. When the SSID is broadcasted, it is included in beacon frames regularly transmitted by the WAP to advertise the availability of the network.
#### WPA:
Again, WPA provides strong encryption and authentication for wireless communications
#### MAC Filtering:
MAC filtering is a security measure that allows a WAP to accept or reject connections from specific devices based on their MAC addresses. By configuring the WAP to accept connections only from devices with approved MAC addresses, it is possible to prevent unauthorized devices from connecting to the network.
#### Deploying EAP-TLS
EAP-TLS is a security protocol used to authenticate and encrypt wireless communications.