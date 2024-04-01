# pwntools

## Basic Setup

```python
from pwn import * #import pwn modules

context.bits = 64 #set the architecture to 64-bits

e = ELF('./filename') #load filename binary to the script

r = remote('ip', port) #establish connection to remote server
r.close() #close the remote server connection
```

## Sending Data

```python
r.send(data) #send data

r.sendline(data) #send data followed by '\n' (newline)

r.sendafter(pattern, data) #send data after a specified pattern

r.sendlineafter(pattern, data) #send data after a specified pattern followed by '\n'
```

## Receiving Data

```python
r.recv(n) #receive n bytes of data, receive as much as posible if n not specified

r.recvline() #receive data until '\n'

r.recvuntil(delims, drop=True) #receive data until specified delimiter, drop=True is by default

r.recvregex(pattern) #receive and return data that matches the pattern

r.recvall() #receive all data until connection close

r.recvline_startswith(prefix) #receive line starts with the specified prefix until '\n'
```

## Format String Helper

```python
# Generate a format string payload
fmtstr_payload(offset, writes, numbwritten=0, write_size='byte')

# To write a single value in specified offset
fmtstr_make_fmt(offset, value, numbwritten=0, write_size='byte')

# To change the value on spesific value with a new value
fmtstr_diff(offset, original, new, numbwritten=0, write_size='byte')

# Automate the process of finding the correct offset to exploit
fmtstr_fuzz(offset, n=1, writes=None, numbwritten=0, write_size='byte')

# To overwrite a spesific return address
fmtstr_vuln(offset, numbwritten=0, write_size='byte')

# offset - where the exploit should start on the stack eg. 14
# writes - what data to write with eg. {0x404060:0x67616c66}
# numbwritten - specified the number of byte written
```
