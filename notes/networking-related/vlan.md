# VLAN

## Creating VLANs

```
S1(config)# vlan 10    //assign vlan id
S1(config-vlan)# name TEST    //assign vlan name
```

***

## Access Port

```
S1(config)# vlan 99
S1(config-vlan)# name Guests
S1(config-vlan)# int <interfaces>
S1(config-if)# switchport mode access    //manually configure a port as an access port

S1(config-if)# switchport acces vlan 99             //specific VLAN is 
S1(config-if)# switchport acces vlan name Guests    //associated to the port
```

***

## Trunk Port

```
S1(config)# int <interface>
S1(config-if)# switchport mode trunk
S1(config-if)# switchport trunk allowed vlan <vlan-list>
```

***

