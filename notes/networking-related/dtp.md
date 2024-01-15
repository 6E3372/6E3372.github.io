---
description: Dynamic Trunking Protocol
---

# DTP

## Enable on interface

```
S1(config-if)# switchport mode dynamic <mode>
```

<table><thead><tr><th width="154">mode</th><th>Description</th></tr></thead><tbody><tr><td>desirable</td><td>The interface will actively attempt to convert the link to a trunk, and it will actively accept the conversion to a trunk.</td></tr><tr><td>auto</td><td>The interface will actively attempt to convert the link to a trunk.</td></tr></tbody></table>

***

## Disable on interface

```
S1(config-if)# switchport nonegotiate
```

***

## Verify

```
S1# show interfaces <int_id> switchport
```
