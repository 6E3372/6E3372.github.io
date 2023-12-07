# Nogard 3

***

<figure><img src="../../../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

***

### Solution

<figure><img src="../../../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

Open the file using Ghidra and check the main function.

<figure><img src="../../../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

Notice that at line 16–17 checks the input we enter before giving us the flag. Here, we must count the value of the variables local\_20, local\_1c, local\_18, and local\_14 before input to the program based on these condition :&#x20;

```c
local20 = 0x133
local20 + local14 * 3 = 0xad8
local1c * local18 * 3 = 0x132b340
local18 * 0x123 + local14 = 0xf01ea
```

Input the value in sequence and you will get the flag

<figure><img src="../../../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

***

### Flag

SKR{XXXXXXXXXXXXXXX}
