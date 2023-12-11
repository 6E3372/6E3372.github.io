# Designing a Network Topology

## Topology

* A map of an internetwork that indicates segments, interconnection points and user communities
* Structure of the network

## Network Design

Two basic types of network design

* Flat
* Hierarchical + Modular

### Flat

* all connecting devices are on the same level
* appropriate for a small and static network
* flat network is a single collision domain
* there is a limit to the number of stations that can be supported

<figure><img src="../../../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

### Hierarchical

* Develop in discrete layers
* Each has a specific functions

why?

* Reduces workload on network devices
* Minimize costs by buying appropriate internetworking devices for each layer
* Keep design element simple and easy to understand
* Facilitates design changes
* Facilitates scaling to a larger size

<figure><img src="../../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

#### Core Layer

* Should design with redundant components because it is critical for interconnectivity
* Highly reliable and adaptable to changes
* Use routing features that optimize packet throughput

#### Distribution Layer

* Can redistribute between bandwidth-intensive accesslayer routing protocols and optimized core routing protocols
* Can summarize routes from the access layer
* Can provide address translation

#### Access Layer

* Provides users on local segments access to the internetwork
* Can include AP, switches, bridges and sharedmedia hubs

## Cisco’s Enterprise Composite Network Model

<figure><img src="../../../../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>
