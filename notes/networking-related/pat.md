---
description: Port Address Translation
---

# PAT

### Using single IPv4 address

{% code lineNumbers="true" %}
```
R1(config)# ip nat inside source list 1 interface serial 0/1/0 overload
R1(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R1(config)# interface serial0/1/0
R1(config-if)# ip nat inside
R1(config-if)# exit
R1(config)# interface Serial0/1/1
R1(config-if)# ip nat outside
```
{% endcode %}

### Using an Address Pool

```
R1(config)# ip nat pool NAT-POOL2 209.165.200.226 209.165.200.240 netmask 255.255.255.224
R1(config)# access-list 1 permit 192.168.0.0 0.0.255.255
R1(config)# ip nat inside source list 1 pool NAT-POOL2 overload
R1(config)# interface serial0/1/0
R1(config-if)# ip nat [inside | outside]
R1(config-if)# interface serial0/1/0
R1(config-if)# ip nat [inside | outside]
```
