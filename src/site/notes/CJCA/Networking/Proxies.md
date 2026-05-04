---
{"dg-publish":true,"permalink":"/cjca/networking/proxies/","created":"2026-03-31T07:12:41.426+01:00","dg-note-properties":{}}
---

#### Proxies

A proxy is when a device or service sits in the middle of a connection and acts as a mediator. The `mediator` is the critical piece of information because it means the device in the middle must be able to inspect the contents of the traffic. Without the ability to be a `mediator`, the device is technically a `gateway`, not a proxy.
*Proxies will almost always operate at Layer 7 of the OSI Model. There are many types of proxy services, but the key ones are:*
-   `Dedicated Proxy`  /  `Forward Proxy`
-   `Reverse Proxy`
-   `Transparent Proxy`

## Forward proxy:
Is when a client makes a request and the computer carries out it.
<mark style="background: #BBFABBA6;">For example, in a corporate network, sensitive computers may not have direct access to the Internet. To access a website, they must go through a proxy (or web filter).</mark>

- Web Browsers like Internet Explorer, Edge, or Chrome all obey the "System Proxy" settings by default.
- Firefox does not use `WinSock` and instead uses `libcurl`, which enables it to use the same code on any operating system.
![[Attachments/Pasted image 20260401183607.png \| 350]]

## Reverse Proxy

A `reverse proxy`, is the reverse of a `Forward Proxy`. Instead of being designed to filter outgoing requests, it filters incoming ones. The most common goal with a `Reverse Proxy`, is to listen on an address and forward it to a closed-off network.
Another common Reverse Proxy is `ModSecurity`, a `Web Application Firewall` (`WAF`). Web Application Firewalls inspect web requests for malicious content and block the request if it is malicious.
 [ModSecurity Core Rule Set](https://owasp.org/www-project-modsecurity-core-rule-set/), as its a great starting point. <mark style="background: #FFB8EBA6;"> Cloudflare, also can act as a WAF but doing so requires letting them decrypt HTTPS Traffic, which some organizations may not want.</mark>
 ![[Attachments/Pasted image 20260401194412.png \| 350]]
 
 All these proxy services act either `transparently` or `non-transparently`.
 - With a `transparent proxy`, <mark style="background: #BBFABBA6;">the client doesn't know about its existence. </mark>The transparent proxy intercepts the client's communication requests to the Internet and acts as a substitute instance.
 - If it is a `non-transparent proxy`, we must be informed about its existence. For this purpose, we and the software we want to use are given a special proxy configuration that ensures that traffic to the Internet is first addressed to the proxy. If this configuration does not exist, we cannot communicate via the proxy.