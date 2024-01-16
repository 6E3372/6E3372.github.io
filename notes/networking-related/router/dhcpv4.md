---
description: Dynamic Host Configuration Protocol
---

# DHCPv4

```
R1(config)# ip dhcp pool <pool_name>    //eg. TESTPOOL
R1(dhcp-config)# network <network_address> <subnet_mask>
R1(dhcp-config)# default-router <default_gateway>
R1(dhcp-config)# dns-server <dns_server_ip>
R1(dhcp-config)# lease <days> <hours> <minutes>

//optional for excluded address range
R1(config)# ip dhcp excluded-address <start_ip> <end_ip>
```

***

## Enable DHCP on Interfaces

```
R1(config)# interface <interface>
R1(config-if)# ip address dhcp
R1(config-if)# exit
```
