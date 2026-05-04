---
{"dg-publish":true,"permalink":"/cjca/linux/network-torubleshooting/","created":"2026-05-04T10:58:32.503+01:00","dg-note-properties":{}}
---

Network troubleshooting is an essential process that involves diagnosing and resolving network issues that can adversely affect the performance and reliability of the network.

Some of the most commonly used tools include:
1. Ping
2. Traceroute
3. Netstat
4. Tcpdump
5. Wireshark
6. Nmap

###### ping
is a command-line tool used to test connectivity between two devices. It sends packets to a remote host and measures the time to return them. 
```
ping 8.8.8.8
```
(Pining google DNS server, sends ICMP packets)

###### traceroute
 traces the route packets take to reach a remote host. It sends packets with increasing Time-to-Live (TTL) values to a remote host and displays the IP addresses of the devices that the packets pass through.
```
 traceroute www.inlanefreight.com
```
![Attachments/Pasted image 20260504100808.png](/img/user/CJCA/Linux/Attachments/Pasted%20image%2020260504100808.png)
 It displays the IP addresses of all intermediary devices the packets traverse. Each line of the traceroute output contains valuable information, offering insights into the network route and performance.
In this example, the destination host is 134.209.24.248, and the maximum number of hops allowed is 30. 
The second line shows the first hop in the traceroute, which is the local network gateway with the IP address 10.80.71.5, followed by the next three columns show the time it took for each of the three packets sent to reach the gateway in milliseconds (2.716 ms, 2.700 ms, and 2.730 ms).

Next, we see the second hop in the traceroute. *However, there was no response from the device at that hop, indicated by the three asterisks instead of the IP address.* This could mean the device is down, blocking ICMP traffic, or a network issue caused the packets to drop.

###### netstat
is used to display active network connections and their associated ports. It can be used to identify network traffic and troubleshoot connectivity issues.
