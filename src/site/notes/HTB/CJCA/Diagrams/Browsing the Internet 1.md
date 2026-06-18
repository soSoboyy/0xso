---
{"dg-publish":true,"permalink":"/htb/cjca/diagrams/browsing-the-internet-1/","tags":["excalidraw"],"dg-note-properties":{"excalidraw-plugin":"parsed","tags":["excalidraw"]}}
---

==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Browsing the internet
{ #eWOUqqqk}


Your browser generates an HTTP request.
The request is encapsulated with TCP, specifying the destination port 80 or 443.
The packet includes the destination IP address 93.184.216.34.
On the local network, our computer uses ARP to find the MAC address of the default gateway (router).

{ #4tlYRtl2}


DNS lookup
{ #vcW8UvRT}


Domain name --> Ip address
{ #q5ojtAVf}


The data frame is sent to the router's MAC address.
The router forwards the packet toward the destination IP address.
Intermediate routers continue forwarding the packet based on the IP address.
{ #jSRwmKex}


Data transmission
{ #wEXS1ZdB}


the server receives the packet and directs it to the application listening on port 80 or 443.
The server processes the HTTP request and sends back a response following the same path in reverse.
{ #E7y9dFQl}


Server
Processing
{ #XYHeZEKg}


the server sends the response back to the client’s temporary port, which was randomly selected by the client’s operating system at the start of the session.
The response follows the reverse path back through the network, being directed from router to router based on the source IP address and port information until it reaches the client.
{ #QDtKGQJq}


Response transmission
{ #H4ND2coM}


