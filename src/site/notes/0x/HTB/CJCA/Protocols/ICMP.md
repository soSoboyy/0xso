---
{"dg-publish":true,"permalink":"/0x/htb/cjca/protocols/icmp/","created":"2026-04-03T12:24:53.391+01:00","dg-note-properties":{}}
---

###### Internet control message protocol is used by devices to communicate with each other on the Internet.
*It sends requests and messages between devices, which can be used to report errors or provide status information.*
- ##### ICMP Requests:
	- A request is a message sent by one device to another to request information or perform a specific action. 
	- The most used type is **ping request** to test connectivity
	- When one device sends a ping request to another, the second device responds with a `ping reply` message.
	- Request  types:
		- `echo request` --> *traceroute* on LInux
		- `timestamp`
		- Address Mask Request
	

- ##### ICMP Messages:
	- A message in ICMP can be either a request or a reply. 
	- In addition to ping requests and responses, <mark style="background: #BBFABBA6;">ICMP supports other types of messages,</mark> such as :
		- error messages,
		- `destination unreachable`, 
		- and `time exceeded` messages.

Another crucial part of ICMP for us is the [Time-To-Live](https://en.wikipedia.org/wiki/Time_to_live) (`TTL`) field in the ICMP packet header that limits the packet's lifetime as it travels through the network.
- It prevents packets circulating indefinitely in the network
- <mark style="background: #BBFABBA6;">each time a packet passes through a network, it decrements the TTL value by 1</mark>
- When value is 0  , router discard packet and sends time exceed message to sender

<mark style="background: #BBFABBA6;">However, it is also possible to guess the operating system based on the default `TTL` value used by the device. Each operating system typically has a default `TTL` value when sending packets.</mark>
