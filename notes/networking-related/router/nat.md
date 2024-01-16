---
description: Network Address Translation
---

# NAT

## Static NAT

```
//config static NAT statement
R1(config)# ip nat inside source static <private ip> <public ip>

R1(config)# int serial 0/1/0
R1(config-if)# ip nat inside
R1(config-if)# exit
R1(config)# int serial 0/1/1
R1(config-if)# ip nat outside

//inside for private
//outside for public
```

***

## Dynamic NAT

### Config

Step 1 : Define the pool of addresses that will be used for translation.

Step 2 - Configure a standard ACL to identify (permit) only those addresses that are to be translated.

Step 3 - Bind the ACL to the pool, using the ip nat inside source list command.

Step 4 - Identify which interfaces are inside.

Step 5 - Identify which interfaces are outside.

```
//create a pool of public ip address
R1(config)# ip nat pool <pool name> <public ip from> <public ip to> netmask <mask>

//creat ACL that determine the IP address that are allowed to be translated
R1(config)# access-list 1 permit 192.168.0.0 0.0.255.255

//config NAT statement
R1(config)# ip nat inside source list 1 pool <pool name>

//define inside outside interfaces
R1(config)# interface serial 0/1/0
R1(config-if)# ip nat inside
R1(config-if)# interface serial 0/1/1
R1(config-if)# ip nat outside
```

***

### Verify and Troubleshoot

```
R1# sh ip nat translations //shows active NAT
R1# sh ip nat statistics
R1# debug ip nat
```
