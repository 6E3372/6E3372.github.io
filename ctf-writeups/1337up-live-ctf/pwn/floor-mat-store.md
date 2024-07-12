---
description: Format String Vulnerability
---

# Floor Mat Store

***

<figure><img src="../../../.gitbook/assets/image (23).png" alt=""><figcaption></figcaption></figure>

***

### Solution

Given an ELF 64-bit file

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

with some protections

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

When looking at the program, it it pretty straight forward where the vulnerable is.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

User need to choose a floor mat and then enter their shipping address. The `Please enter your shipping address:` is vulnerable to Format String Attack because it use printf() to display the shipping address at `Your floor mat will be shipped to:`. I spammed `%p` until i get the leaked memory. I notice that when we choose floor mat number 1-5, the memory leaked is just nothing. :cry:

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption><p>Need trial and error for the leaked memory for floor mat number 1-5</p></figcaption></figure>

There is a hidden number which is 6, its memory leaked contains the flag.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

So, put the hex in CyberChef and let it cook :man\_cook:

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Just play a little bit with the binary and word length byte

Btw, it is good challenge tho. At first, I didn't even notice the program accept the number 6 :rofl:

***

### Flag

INTIGRITI{50\_7h475\_why\_7h3y\_w4rn\_4b0u7\_pr1n7f}
