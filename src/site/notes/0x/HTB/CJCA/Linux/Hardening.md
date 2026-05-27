---
{"dg-publish":true,"permalink":"/0x/htb/cjca/linux/hardening/","created":"2026-05-05T06:42:51.224+01:00","dg-note-properties":{}}
---

#hardening
Three such mechanisms are SELinux, AppArmor, and TCP wrappers:
#### Security-Enhanced Linux
Security-Enhanced Linux (`SELinux`) is a mandatory access control (`MAC`) system integrated into the Linux kernel. I*t provides fine-grained control over access to system resources and applications by enforcing security policies.* *These policies define the permissions for each process and file on the system.*
<mark style="background: #BBFABBA6;"> SELinux is deeply integrated into the kernel and offers more detailed security controls, but it can be more complex to configure and maintain.</mark>
#### AppArmor
Like SELinux, `AppArmor` is a MAC system that controls access to system resources and applications, but it operates in a simpler, *more user-friendly manner*. AppArmor is implemented as a Linux Security Module (`LSM`) and uses application profiles to define what resources an application can access.
<mark style="background: #BBFABBA6;">AppArmor operates as a kernel module and uses profile-based security</mark>
#### TCP Wrappers

`TCP wrappers` are a host-based network access control tool that restricts access to network services based on the IP address of incoming connections. When a network request is made, TCP wrappers intercept it, checking the request against a list of allowed or denied IP addresses.
*TCP wrappers are an excellent tool for basic network-level protection.*

##### Exercises:

|1.|Install SELinux on your VM.|
|2.|Configure SELinux to prevent a user from accessing a specific file.|
|3.|Configure SELinux to allow a single user to access a specific network service but deny access to all others.|
|4.|Configure SELinux to deny access to a specific user or group for a specific network service.|
|5.|Configure AppArmor to prevent a user from accessing a specific file.|
|6.|Configure AppArmor to allow a single user to access a specific network service but deny access to all others.|
|7.|Configure AppArmor to deny access to a specific user or group for a specific network service.|
|8.|Configure TCP wrappers to allow access to a specific network service from a specific IP address.|
|9.|Configure TCP wrappers to deny access to a specific network service from a specific IP address.|
|10.|Configure TCP wrappers to allow access to a specific network service from a range of IP addresses.|
