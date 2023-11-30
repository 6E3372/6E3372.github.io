# Concepts

### Intro

* ACL (Access Control List)
* A series of IOS commands that are used to filter packets based on information found in the packet header

<details>

<summary>Task performed by router that requires ACLs to identify traffic</summary>

* Limit network traffic to increase network performance
* Provide traffic flow control
* Provide a basic level of security for network access
* Filter traffic based on traffic type
* Screen hosts to permit or deny access to network services
* Provide priority to certain classes of network traffic

</details>

***

### Packet Filtering

* Packet filtering controls access to a network by analyzing the incoming and/or outgoing packets and forwarding them or discarding them based on given criteria.
* Packet filtering occurs at [Layer 3](#user-content-fn-1)[^1] or [Layer 4](#user-content-fn-2)[^2]
* Cisco routers support two types of ACL
  * **Standard ACLs**
    * ACLs only filter at Layer 3 using the source IPv4 address only.
  * **Extended ACLs**
    * ACLs filter at Layer 3 using the source and / or destination IPv4 address. They can also filter at Layer 4 using TCP, UDP ports, and optional protocol type information for finer control.
*

[^1]: Network Layer

[^2]: Transport Layer
