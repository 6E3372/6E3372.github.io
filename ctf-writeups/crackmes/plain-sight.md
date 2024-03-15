# Plain Sight

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

***

## Solution

An ELF 64-bits given

<figure><img src="../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

The program need a password to verify be verified

<figure><img src="../../.gitbook/assets/image (5).png" alt=""><figcaption></figcaption></figure>

Open Ghidra, analyse the code.

As we see below, the `main` function called `Login` function.

<figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

So, at `Login` function, we can see it checks for a password at line 16, where the program will return "Welcome!" if we input the password _do\_not\_hardcode_.

<figure><img src="../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>
