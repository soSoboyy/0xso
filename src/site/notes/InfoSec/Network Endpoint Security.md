---
{"dg-publish":true,"permalink":"/info-sec/network-endpoint-security/","dg-note-properties":{}}
---


### Firewalls
The firewall is an important complement to host-based security services such as intrusion detection systems. Typically, a firewall is inserted between the premises network and the Internet to establish a controlled link and to erect an outer security wall or perimeter.

**Firewall Characteristics**
1. All traffic from inside to outside, and vice versa, must pass through the firewall. This is achieved by physically blocking all access to the local network except via the firewall. Various configurations are possible, as explained later in this section.
    
2. Only authorised traffic, as defined by the local security policy, will pass. Various types of firewalls are used to implement various types of security policies, as explained later in this chapter.
    
3. The firewall itself is immune to penetration. This implies using a hardened system with a secured operating system (OS). Trusted computer systems are suitable for firewall hosting and are often required in government applications.

#### Four techniques firewalls use to control access and enforce the site’s security policy:

- Service control: Determines the types of Internet services that can be accessed, inbound or outbound. The firewall may filter traffic based on IP address, protocol, or port number; may provide proxy software that receives and interprets each service request before passing it on; or may host the server software itself, such as a Web or mail service.

- Direction control: Determines the direction in which particular service requests may be initiated and allowed to flow through the firewall.

- User control: Controls access to a service according to which user is attempting to access it. This feature is typically applied to users inside the firewall perimeter (local users). It may also be applied to incoming traffic from external users; the latter requires secure authentication technology, such as the one provided in IPsec.

- Behaviour control: Controls how particular services are used. For example, the firewall may filter email to eliminate spam or enable external access to only a portion of the information on a local Web server.