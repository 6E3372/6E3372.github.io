# STP

## Adjust STP Priority

```
S1(config)# spanning-tree vlan <vlan-id> priority <priority>
```

***

## Config PortFast

```
S1(config)# spanning-tree portfast

OR

S1(config)# int <interface>
S1(config-if)# spanning-tree portfast
```

***

## Config BPDU Guard

```
S1(config)# spanning-tree bpduguard enable

OR

S1(config)# int <interface>
S1(config-if)# spanning-tree bpduguard enable
```

***

## Config Root Guard

```
S1(config)# spanning-tree guard root

OR

S1(config)# int <interface>
S1(config-if)# spanning-tree guard root
```

***

## Config Etherchannel with STP PortFast

```
S1(config)# spanning-tree portfast bpduguard default
```

***

## Verify

```
S1# sh spanning-tree
S1# sh spanning-tree root    //verify Root ID and Root Port
```
