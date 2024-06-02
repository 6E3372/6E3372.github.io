# Don't Go Overboard

***

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### Solution

For this challenge, you need to find the right offset so that it will overflow the buffer.

So, I found it at 30 bytes but it still doesn't give me the flag:disappointed\_relieved:

I decompile the code using Ghidra and look at the main function.

At line 16, the program checks the argument of `0` and `5`.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

So, I include `05` in my payload, which is 30 bytes of the letter `a`.

Like this `aaaaaaaaaaaaaaaaaaaaaaaaaaaaaa05`

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### Flag

CURTIN\_CTF{T@RG3TT3D\_0V3RF10W}
