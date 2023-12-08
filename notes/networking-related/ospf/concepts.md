# Concepts

## Features & Characteristics

### Introduction

* OSPF (Open Short Path First)
* A link-state routing protocol that uses the concept of areas
* Information about the state of a link[^1] is known as a link-state[^2]

***

### OSPF Components

* All routing protocol shared a similar component which is [routing protocol messages](#user-content-fn-3)[^3] to exchange route information
* There are 5 types of[ packet](#user-content-fn-4)[^4] for routers that running OSPF to exchange message to convey routing information
  * Hello packet
  * Database description packet
  * Link-state request packet
  * Link-state update packet
  * Link-state acknowledgment packet
* OSPF messages used to create and maintain these OSPF database

<table><thead><tr><th width="142.66666666666663">Database</th><th width="165">Table</th><th>Description</th></tr></thead><tbody><tr><td>Adjacency Database</td><td>Neighbor Table</td><td><ul><li>List of all neighbor routers to which a router has established bi-directional communication.</li><li>This table is unique for each router.</li><li>Can be viewed using the <code>show ip ospf neighbor</code> command.</li></ul></td></tr><tr><td>Link-state Database (LSDB)</td><td>Topology Table</td><td><ul><li>Lists information about all other routers in the network.</li><li>The database represents the network LSDB.</li><li>All routers within an area have identical LSDB.</li><li>Can be viewed using the <code>show ip ospf database</code> command</li></ul></td></tr><tr><td>Forwarding Database</td><td>Routing Table</td><td><ul><li>List of routes generated when an algorithm is run on the link-state database.</li><li>Each router's routing table is unique and contains information on how and where to send packets to other routers.</li><li>Can be viewed using the <code>show ip route</code> command</li></ul></td></tr></tbody></table>

***

### Link-State Operation

The following are the link-state routing steps that are completed by a router to maintain routing information to reach a state of convergence:

1. Establish Neighbor Adjacencies
2. Exchange Link-State Advertisements
3. Build the Link State Database
4. Execute the SPF Algorithm
5. Choose the Best Route

***

### Single Area OSPF

* All routers are in one area. Best practice is to use area 0

<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

***

### Multiarea OSPF

* OSPF is implemented using multiple areas, in a hierarchical fashion.&#x20;
* All areas must connect to the backbone area (area 0).
* Routers interconnecting the areas are referred to as Area Border Routers (ABRs)

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

<table><thead><tr><th width="248">Advantage</th><th>Explaination</th></tr></thead><tbody><tr><td>Smaller routing tables</td><td>Tables are smaller because there are fewer routing table entries. This is because network addresses can be summarized between areas. Route summarization is not enabled by default.</td></tr><tr><td>Reduced link-state update overhead</td><td>Designing multiarea OSPF with smaller areas minimizes processing and memory requirements.</td></tr><tr><td>Reduced frequency of SPF calculations</td><td>Multiarea OSPF localize the impact of a topology change within an area. For instance, it minimizes routing update impact because LSA flooding stops at the area boundary.</td></tr></tbody></table>

***

### OSPFv3

* OSPFv3 has the same functionality as OSPFv2 but uses IPv6 as the network layer transport.
* It communicates with OSPFv3 peers and advertises IPv6 routes, using the SPF algorithm to determine the best paths throughout the routing domain.
* OSPFv3 runs independently from its IPv4 counterpart, even though the processes and operations are basically the same

***

## Operation

### OSPF Operational State

<table><thead><tr><th width="152">State</th><th>Description</th></tr></thead><tbody><tr><td>Down</td><td><ul><li>No Hello packets received = Down.</li><li>Router sends Hello packets.</li><li>Transition to Init state</li></ul></td></tr><tr><td>Init</td><td><ul><li>Hello packets are received from the neighbor.</li><li>They contain the Router ID of the sending router.</li><li>Transition to Two-Way state.</li></ul></td></tr><tr><td>Two-Way</td><td><ul><li>In this state, communication between the two routers is bidirectional.</li><li>On multiaccess links, the routers elect a DR and a BDR.</li><li>Transition to ExStart state</li></ul></td></tr><tr><td>ExStart</td><td><ul><li>On point-to-point networks, the two routers decide which router will initiate the DBD packet exchange and decide upon the initial DBD packet sequence number.</li></ul></td></tr><tr><td>Exchange</td><td><ul><li>Routers exchange DBD packets.</li><li>If additional router information is required then transition to Loading; otherwise, transition to the Full state</li></ul></td></tr><tr><td>Loading</td><td><ul><li>LSRs and LSUs are used to gain additional route information.</li><li>Routes are processed using the SPF algorithm.</li><li>Transition to the Full state.</li></ul></td></tr><tr><td>Full</td><td>The link-state database of the router is fully synchronized</td></tr></tbody></table>

***

### Sync OSPF Database

After the Two-Way state, routers transition to database synchronization states. Three steps as follows :&#x20;

1. **Decide first router:** The router with the highest router ID sends its DBD first.
2. **Exchange DBDs:** As many as needed to convey the database. The other router must acknowledge each DBD with an LSAck packet.
3. **Send an LSR:** Each router compares the DBD information with the local LSDB. If the DBD has more current link information, the router transitions to the loading state.

After all LSRs have been exchanged and satisfied, the routers are considered synchronized and in a full state. [Updates (LSUs) are sent.](#user-content-fn-5)[^5]

[^1]: A link is an interface on a router, a network segment that connects two routers, or a stub network such as an Ethernet LAN that is connected to a single router

[^2]: includes the network prefix, prefix length, and cost

[^3]: The messages help build data structures, which are then processed using a routing algorithm

[^4]: These packets are used to discover neighboring routers and also to exchange routing information to maintain accurate information about the network

[^5]: * When a change is perceived (incremental updates)
    * Every 30 minutes
