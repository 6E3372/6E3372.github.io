# Configuration

### Numbered Standard IPv4 ACL Syntax

{% code overflow="wrap" %}
```
R1(config)# access-list <access list num> {deny | permit | remark text} source [source wildcard] [log]
```
{% endcode %}

<table><thead><tr><th width="179">Parameter</th><th>Description</th></tr></thead><tbody><tr><td>access list num</td><td>Number range is 1 to 99 or 1300 to 1999</td></tr><tr><td>deny</td><td>Denies access if the condition is matched</td></tr><tr><td>permit</td><td>Permits access if the condition is matched</td></tr><tr><td>remark text</td><td>(Optional) text entry for documentation purposes</td></tr><tr><td>source</td><td>Identifies the source network or host address to filter</td></tr><tr><td>source-wildcard</td><td>(Optional) 32-bit wildcard mask that is applied to the source</td></tr><tr><td>log</td><td>(Optional) Generates and sends an informational message when the ACE is matched</td></tr></tbody></table>

### Named Standard IPv4 ACL Syntax

```
R1(config)# ip access-list standard <access list name>
//ACL names are alphanumeric, case sensitive, and must be unique eg. NOACCESS
```

