---
description: Hot Standby Router Protocol
---

# HSRP

## Define Group

```
R1(config)# int <interface>
R1(config-if)# standby <group_num> ip <ip>    //config hsrp group
R1(config-if)# standby <group_num> mac-address <mac_address>    //spesify mac address
R1(config-if)# standby <group_num> priority <priority>    //highest priority become active router
R1(config-if)# standby <group_num> timers <hello_time> <hold_time>
R1(config-if)# standby <group_num> preempt    //optional
```
