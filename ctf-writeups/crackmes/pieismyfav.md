# PieIsMyFav

<figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption></figcaption></figure>

***

## Solution

This challenge is pretty easy. Given an ELF file

<figure><img src="../../.gitbook/assets/image (74).png" alt=""><figcaption></figcaption></figure>

It needs to validate a number, but not just any number.

<figure><img src="../../.gitbook/assets/image (75).png" alt=""><figcaption></figcaption></figure>

Dissamble the program using Ghidra, i can see it checks the number with some calculations

<figure><img src="../../.gitbook/assets/image (76).png" alt=""><figcaption><p>Line 17 is where the numbers are calculated</p></figcaption></figure>

To sum up, the calculation looks like this.

`number = (14 + 100 x 3) / 100`

So the number calculated is `3.42`

<figure><img src="../../.gitbook/assets/image (77).png" alt=""><figcaption></figcaption></figure>

p/s: i know nothing about the language but im pretty sure it is portugese and it says "correct" :rofl:
