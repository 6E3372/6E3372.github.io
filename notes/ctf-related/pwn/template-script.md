---
description: just a simple script made in python for pwn challenges
---

# Template Script

{% code title="template.py" %}
```python
from pwn import *

elf = context.binary = ELF('./filename', checksec=False)
p = process()
#p = remote('ip', port)

# Exploit goes here
offset = 10
payload = b'A'*offset

p.sendline(payload)
p.interactive()
```
{% endcode %}
