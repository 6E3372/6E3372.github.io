# b2r/koth

## Start

### Scan ports

```bash
nmap <ip>
#or
nmap -A -T4 <ip>
```

### Nikto

```bash
nikto -h <ip>
```

### SMB

```bash
enum4linux <ip>
```

### Search directories

```bash
gobuster dir -u <ip> -w /usr/share/wordlists/dirb/common.txt
```

***

## Password Cracking

### JohnTheRipper

```bash
john --wordlist=</path/to/rockyou.txt> --format=<format> <hash key>
```

### ssh2john

```bash
ssh2john <filename> 
#id_rsa to hash
```

***

## RevShell

{% embed url="https://www.revshells.com/" %}

***

## PrivEsc

```bash
sudo -l 
#look for anything intersting
```

{% embed url="https://gtfobins.github.io/" %}
might help a lot!
{% endembed %}

***

## Defend The Title :crown:

```bash
chattr +i /root/king.txt
#immune the root file
```

```bash
netstat -nlp | grep <port>
#find process that run on x port

ps -p <PROCESS ID>
#search for PID

kill -9 <PROCESS ID>
#kill for the win
```

***

## Other

### Interactive TTY

```bash
python -c 'import pty; pty.spawn("/bin/bash")'
```

```bash
#in revshell
$ python -c 'import pty; pty.spawn("/bin/bash")'
CTRL-Z

#in kali
$ stty raw -echo
$ fg

#in revshell
$ reset
$ export SHELL=bash
$ export TERM=xterm-256color
$ stty rows <num> columns <cols>
```
