---
description: '*need a redo'
---

# Etherchannel

## Static etherchannel

```
S1(conf-if)# channel-group <etherchannel-id> mode on
```

***

## Enable

{% tabs %}
{% tab title="LACP" %}
```
S1(config-if)# channel-group <etherchannel-id> mode <mode>
```

<table><thead><tr><th width="112">mode</th><th>Description</th></tr></thead><tbody><tr><td>active</td><td>The interface actively negotiates the formation of an EtherChannel.</td></tr><tr><td>passive</td><td>The interface passively waits for the other side to initiate EtherChannel negotiation.</td></tr></tbody></table>
{% endtab %}

{% tab title="PAgP" %}
```
S1(config-if)# channel-group <etherchannel-id> mode <mode>
```

<table><thead><tr><th width="150">mode</th><th>Description</th></tr></thead><tbody><tr><td>auto</td><td>The interface will passively wait for EtherChannel negotiation</td></tr><tr><td>desirable</td><td>The interface will actively initiate EtherChannel negotiation</td></tr></tbody></table>
{% endtab %}
{% endtabs %}

***

## LACP

### Rate

```
S1(config-if)# lacp rate <rate>
```

<table><thead><tr><th width="165">rate</th><th>Description</th></tr></thead><tbody><tr><td>fast</td><td>LACP packets are sent every second</td></tr><tr><td>normal</td><td>LACP packets are sent every 30 seconds (default)</td></tr></tbody></table>

### Priority

```
S1(config)# lacp port-priority <priority>
S1(config)# lacp system-priority <priority>
```

### Etherchannel Load Balancing Hash Algorithm

```
```
