# Configuration

### Standard IPv4 ACL Syntax

{% code overflow="wrap" %}
```
R1(config)# access-list <acl num> <action> <source> <source wildcard>
```
{% endcode %}

<table><thead><tr><th width="179">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>acl num</td><td>Number range is 1 to 99 or 1300 to 1999</td></tr><tr><td>action</td><td>deny, permit, remark text</td></tr><tr><td>source</td><td>Identifies the source network or host address to filter</td></tr><tr><td>source-wildcard</td><td>(Optional) 32-bit wildcard mask that is applied to the source</td></tr></tbody></table>

### Extended IPv4 ACL Syntax

```
R1(config)# access-list <acl number> <action> <protocol> <source> <wildcard source> <destination> <wildcard destination>
```

<table><thead><tr><th width="193">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>acl number</td><td>100-199 and 2000-2699</td></tr><tr><td>action</td><td>deny, permit, remark text</td></tr><tr><td>protocol</td><td>tcp,icmp,udp</td></tr></tbody></table>
