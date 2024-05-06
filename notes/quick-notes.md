---
description: >-
  Purposely for my ip routing test. very last minute notes. might delete soon
  (wish me luck tho)
---

# Quick Notes

## DHCP for IPv4

* Operations
  * Discover
    * Send broadcast DHCPDISCOVER message to destination IP 255.255.255.255 and destination MAC FFFF:FFFF:FFFF. Source IP is 0.0.0.0 and MAC address of sending device
  * Offer
    * Respond with DHCPOFFER message with an unleased IP address, subnet mask, and default gateway information
  * Request
    * Sending a DHCPREQUEST message to request the use the offered IP
  * Ack
    * Respong with DHCPACK message to acknowledge the use of that IP



***

## EIGRP

* Enhanced Interior Gateway Routing Protocol
* enhanced distance vector routing protocol commonly found in enterprise networks.

<figure><img src="../.gitbook/assets/image (82).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Successor Router" %}
* The route with the lowest path metric to reach a destination
{% endtab %}

{% tab title="Successor" %}
* The first next-hop router for the successor route.
{% endtab %}

{% tab title="Feasible distance (FD)" %}
* The metric value for the lowest-metric path to reach a destination
*
{% endtab %}

{% tab title="Reported distance (RD)" %}
* Distance reported by a router to reach a prefix
{% endtab %}

{% tab title="Feasibility condition" %}
* For a route to be considered a backup route, the RD received for that route must be less than the FD calculated locally. This logic guarantees a loop-free path.
{% endtab %}

{% tab title="Feasible successor" %}
* A route with that satisfies the feasibility condition is maintained as a backup route
{% endtab %}
{% endtabs %}



### Configuration

#### Classic Config

```
//Enable EIGRP
R1(config)# router eigrp <AS_number> //AS_number is 1 to 65535

//Identify network interfaces
R1(config-router)# network <network_address> <wildcard_mask>
```

#### Named Mode

<details>

<summary><strong>Benefits</strong></summary>

* All the EIGRP configuration occurs in one location

<!---->

* It supports current EIGRP features and future developments

<!---->

* It supports multiple address families (including Virtual Routing and Forwarding \[VRF] instances). EIGRP named configuration is also known as multi-address family configuration mode

<!---->

* Commands are clear in terms of the scope of their configuration.

</details>

```
R1(config)# router eigrp <name>
```

#### Authentication

```
//Authentication
R1(config)# keychain <keychain name>
R1(config-keychain)# key <key number> //key number from 0 to 2147483647
R1(config-keychain-key)# key-string <password>

//Enable auth on int
R1(config-if)# ip authentication key-chain eigrp <as number> <keychain name>
R1(config-if)# ip authentication mode eigrp <as number> md5

//Enable auth on int (named mode)
R1(config-router-af-interface)# authentication mode md5
R1(config-router-af-interface)# authentication key-chain <key chain name>

//Verify
R1# show key chain
```

### Stub Concepts

go [here](https://chat.openai.com/share/68516431-b22d-40d8-a58d-9aa799edb648)

### Path Metric Calculation

<figure><img src="../.gitbook/assets/image (83).png" alt=""><figcaption></figcaption></figure>

By default,

* K1 and K3 are 1
* K2 , K4 , and K5 are 0

<figure><img src="../.gitbook/assets/image (84).png" alt=""><figcaption></figcaption></figure>

### Route Summarization

```
//Config
//Classic
R1(config-if)#ip summary-address eigrp <as number> <network> <subnet mask>

//named mode
R1(config-router-af-interface)# summary-address <network> <subnet mask>
```

### Stub

```
//Config
R1(config-router)# eigrp stub
```

***

## OSPF

basic config[ here](networking-related/router/ospf.md)

### Timer

```
//Hello
R1(config-if)# ip ospf hello-interval <time> //time is from 1-65,535 in seconds

//Dead
R1(config-if)# ip ospf dead-interval <time> //time is from 1-65,535 in seconds
```

### DR/BDR

Too lazy. go [here](https://chat.openai.com/share/a9f3a600-0f80-40e1-8926-1cd3fc5a074c)

### LSA Types

go [here](https://chat.openai.com/share/4a802455-be66-4ad8-99a4-1b35028a3138)

### Stubby Things

go [here](https://chat.openai.com/share/656e1bbd-0727-4af5-9e69-61244a1483f7)
