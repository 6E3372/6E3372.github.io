---
description: Access Control List
---

# ACL

## Standard IPv4 ACL Syntax

{% code overflow="wrap" %}
```
R1(config)# access-list <acl num> <action> <source ip> <source wildcard>
```
{% endcode %}

<table><thead><tr><th width="179">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>acl num</td><td> 1-99 or 1300-1999</td></tr><tr><td>action</td><td>deny, permit, remark text</td></tr></tbody></table>

***

## Extended IPv4 ACL Syntax

```
R1(config)# access-list <acl number> <action> <protocol> <source ip> <wildcard source> <destination ip> <wildcard destination>
```

<table><thead><tr><th width="193">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>acl number</td><td>100-199 or 2000-2699</td></tr><tr><td>action</td><td>deny, permit, remark text</td></tr><tr><td>protocol</td><td>eg. tcp,icmp,udp</td></tr></tbody></table>

***

## Apply ACL on Interface

```
R1(config)# int <interface>
R1(config-if)# ip access group <acl number> <direction>
```

<table><thead><tr><th width="144">direction</th><th>Description</th></tr></thead><tbody><tr><td>in</td><td><ul><li>applied to incoming traffic on that interface</li><li>filtering traffic as it enters the router.</li></ul></td></tr><tr><td>out</td><td><ul><li>applied to outgoing traffic on that interface</li><li>control traffic leaving the router towards the destination.</li></ul></td></tr></tbody></table>
