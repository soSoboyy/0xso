---
{"dg-publish":true,"permalink":"/htb/cjca/internet-architecture/","dg-note-properties":{}}
---

#### P2P:
In a `Peer-to-Peer (P2P`) network, each node, whether it's a computer or any other device, acts as both a client and a server. This setup allows nodes to communicate directly with each other, sharing resources such as files, processing power, or bandwidth, without the need for a central server. 
**A popular example of Peer-to-Peer (P2P) architecture is torrenting, as seen with applications like BitTorrent. In this system, anyone who has the file, referred to as a `seeder`, can upload it, allowing others to download it from multiple sources simultaneously.**

#### Client-Server 
he `Client-Server` model is one of the most widely used architectures on the Internet. 

A key component of this architecture is the **tier model**, which organizes server roles and responsibilities into layers. This enhances scalability and manageability, as well as security and performance.

- #### Single-Tier Architecture
	- In a  `single-tier`  architecture, the client, server, and database all reside on the same machine. (Rarely used in enterprise due to scalability limitations.)
	- The `two-tier` architecture splits the application environment into a client and a server. The client handles the presentation layer, and the server manages the data layer.
	- A `three-tier` architecture introduces an additional layer between the client and the database server, known as the application server. In this model, the client manages the presentation layer, the application server handles all the business logic and processing, and the third tier is a database server.

#### Hybrid Architecture

A  `Hybrid`  model blends elements of both  `Client-Server`  and  `Peer-to-Peer (P2P)`  architectures. In this setup, central servers are used to facilitate coordination and authentication tasks, while the actual data transfer occurs directly between peers.
**When we open a video conferencing app and log in, the credentials (username and password) are verified by central servers, which also manage the session by coordinating who is in the meeting and controlling access. Once we're logged in and the meeting begins, the actual video and audio data is transferred directly between our device and those of other participants, bypassing the central server to reduce lag and enhance video quality. This setup combines both models: it uses the central server for initial connection and control tasks, while the bulk of data transfer occurs in a peer-to-peer style, reducing the server load and leveraging direct, fast connections between peers.**


#### Cloud Architecture

`Cloud Architecture`  refers to computing infrastructure that is hosted and managed by third-party providers, such as AWS, Azure, and Google Cloud. This architecture operates on a virtualized scale following a client-server model. It provides on-demand access to resources such as servers, storage, and applications, all accessible over the Internet.

## Software-Defined Architecture (SDN)

`Software-Defined Networking (SDN)`  is a modern networking approach that separates the control plane, which makes decisions about where traffic is sent, from the data plane, which actually forwards the traffic.
- SDN provides a programmable network management environment, enabling administrators to dynamically adjust network policies and routing as required.
- Large enterprises or cloud providers use SDN to dynamically allocate bandwidth and manage traffic flows according to real-time demands.
## Key Comparisons

Below is a comparison table that outlines key characteristics of different network architectures: 

| Architecture    | Centralized                     | Scalability          | Ease of Management                 | Typical Use Cases                  |
| --------------- | ------------------------------- | -------------------- | ---------------------------------- | ---------------------------------- |
| *P2P*           | Decentralized (or partial)      | High (as peers grow) | Complex (no central control)       | File-sharing, blockchain           |
| *Client-Server* | Centralized                     | Moderate             | Easier (server-based)              | Websites, email services           |
| *Hybrid*        | Partially central               | Higher than C-S      | More complex management            | Messaging apps, video conferencing |
| *Cloud*         | Centralized in provider’s infra | High                 | Easier (outsourced)                | Cloud storage, SaaS, PaaS          |
| *SDN*           | Centralized control plane       | High (policy-driven) | Moderate (needs specialized tools) | Datacenters, large enterprises     |

#### Data Flow Diagram
<mark style="background: #BBFABBA6;">Below is a flow chart showing the complete journey of a user accessing a website on the internet:</mark>

![Network process](https://cdn.services-k8s.prod.aws.htb.systems/content/modules/289/Data_Flow/Data_Flow-1-New.png)
