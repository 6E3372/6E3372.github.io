---
description: VLAN Trunking Protocol
---

# VTP

## Enable

```
S1(config)# vtp mode <mode>
```

<table><thead><tr><th width="147">Mode</th><th>Description</th></tr></thead><tbody><tr><td>server</td><td>This switch will participate in VTP and can add, modify, or delete VLANs.</td></tr><tr><td>client</td><td>This switch will participate in VTP but cannot add, modify, or delete VLANs. It accepts updates from VTP servers.</td></tr><tr><td>transparent</td><td>This switch will not participate in VTP but will forward VTP advertisements.</td></tr><tr><td>off</td><td>This switch does not participate in VTP advertisements and does not forward them out of any ports either.</td></tr></tbody></table>

***

## Set VTP Domain

```
S1(config)# vtp domain <domain name>
```

***

## Set VTP Password

```
S1(config)# vtp password <your password>
```

***

## Assign VTP version

```
S1(config)# vtp version <version>    // 1 or 2
```

***

## Config VTP Pruning

```
S1(config)# vtp pruning    //optimize the broadcast traffic
```

***

## Verify

```
S1# show vtp status
```
