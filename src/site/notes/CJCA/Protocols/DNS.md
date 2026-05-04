---
{"dg-publish":true,"permalink":"/cjca/protocols/dns/","created":"2026-03-27T06:13:13.570+00:00","dg-note-properties":{}}
---

## Domain Name System (DNS)
##### The Domain Name System (DNS) is like the phonebook of the internet. It helps us find the right number (an IP address) for a given name (a domain such as `www.google.com`).
###### DNS is organized like a tree, starting from the root and branching out into different layers.
![[Attachments/Pasted image 20260327062853.png \| 400]]

| Layer                    | Desc                                                                              |
| ------------------------ | --------------------------------------------------------------------------------- |
| Root Servers             | The top of the DNS hierarchy.                                                     |
| Top-Level Domains (TLDs) | Such as `.com`, `.org`, `.net`, or country codes like `.uk`, `.de`.               |
| Second-Level Domains     | For example, `example` in `example.com`.                                          |
| Subdomains or Hostname   | For instance, `www` in `www.example.com`, or `accounts` in `accounts.google.com`. |
<mark style="background: #ADCCFFA6;">When we enter a domain name in our browser, the computer needs to find the corresponding IP address. This process is known as `DNS resolution` or `domain translation`. The steps below show how this process works.</mark>
![[Attachments/Pasted image 20260327062506.png \| 600]]




