# Configuration

## Basic

### Enable OSPFv2

```
R1(config)# router ospf <process-id>    //process id can be from 1-65535
```

***

### Config Loopback as Router ID

```
R1(config-if)# int loopback 1
R1(config-if)# ip address 1.1.1.1 255.255.255.255
R1(config-if)# end
```

***

### Expicitly Config Router ID

```
R1(config)# router ospf 10
R1(config-router)# router id 1.1.1.1
R1(config-router)# end
```

***

### Point-to-Point OSPF

{% tabs %}
{% tab title="Using Network" %}
```
R1(config)# router ospf 10
R1(config-router)# network <network address> <wildcard mask> area <area-id>
// network address eg. 10.10.1.4
// wildcard mask eg. 0.0.0.3
// area-id eg. 0
```
{% endtab %}

{% tab title="Using Quad Mask" %}
```
R1(config)# router ospf 10
R1(config-router)# network <gateway> 0.0.0.0 area <area-id>
//gateway eg. 10.10.1.1
//area-id eg. 0
```
{% endtab %}

{% tab title="Using IP OSPF" %}
```
R1(config)# router ospf 10
R1(config-router)# int g0/0/0
R1(config-if)# ip ospf <process-id> area <area-id>
```
{% endtab %}
{% endtabs %}

***

## Verify&#x20;

```
R1# show ip protocols
R1# show ip route
R1# show ip route ospf
```
