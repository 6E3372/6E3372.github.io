# Config Switch to use SSH

```
S1(config)# ip domain-name <domain name>    //eg. example.com
S1(config)# username <username> password <password>
S1(config)# crypto key generate rsa    //1024
S1(config)# ip ssh version 2
S1(config)# line vty 0 4
S1(config-line)# login local
S1(config-line)# transport input telnet ssh
```
