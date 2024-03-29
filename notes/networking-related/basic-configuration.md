# Basic Configuration

{% code title="For Router and Switch" %}
```
router(config)# hostname R1    //asign name to device

R1(config)# no ip domain lookup    //disable dns lookup

R1(config)# enable secret class    //privileged EXEC encrypted password

R1(config)# line console 0         // Assign 'cisco' as
R1(config-line)# password cisco    // the console password and
R1(config-line)# login             // enable login.

R1(config)# line vty 0 4            // Assign 'cisco' as 
R1(config-line)# password cisco     // the VTY password 
R1(config-line)# login              // and enable login.

R1(config)# service password-encryption    //encrypt plaintext password

R1(config)# banner motd $ Authorized Users Only! $    //creat banner

R1# copy running-config startup-config    //save the config
```
{% endcode %}

***

## Config Loopback

```
R1(config)# int loopback 0
R1(config-if)# ip address <ip> <mask>
```

***

## Config Router Interfaces

```
R1(config)# int g<slot><port> // g0/1
R1(config-if)# ip address <ip> <mask>
R1(config-if)# no shut
R1(config-if)# end
// repeat for other interfaces
```
