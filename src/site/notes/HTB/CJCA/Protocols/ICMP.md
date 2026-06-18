---
{"dg-publish":true,"permalink":"/htb/cjca/protocols/icmp/","dg-note-properties":{}}
---

#ttl #hops 
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
- It prevents packets from circulating indefinitely in the network
- <mark style="background: #BBFABBA6;">each time a packet passes through a network, it decrements the TTL value by 1</mark>
- When value is 0  , the router discards packet and sends time exceed message to the sender

<mark style="background: #BBFABBA6;">However, it is also possible to guess the operating system based on the default `TTL` value used by the device. Each operating system typically has a default `TTL` value when sending packets.</mark>

Example:
1. **Observe the Returned TTL**: Note the value from the ping response (e.g., `ttl=54`).
2. **Round Up to the Nearest Standard Default**: Operating systems typically use specific default starting values. Round your observed value **up** to the nearest common default:
    - **64**: Common for Linux, macOS, Android, and most Unix-like systems.
    - **128**: Common for Windows systems.
    - **255**: Common for network hardware (routers, switches) and some specialised systems.


**Example Calculation**: If you ping a server and get `ttl=54`:
- It is close to 64, not 128.
- **Initial TTL**: 64.
- **Hops Taken**: $64 - 54 = 10$ hops.