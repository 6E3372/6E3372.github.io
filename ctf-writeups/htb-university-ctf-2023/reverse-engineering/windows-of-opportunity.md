---
description: HTB 2023
---

# Windows Of Opportunity

***

<figure><img src="../../../.gitbook/assets/image (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

### Solution

Given a file named **windows**.

{% code overflow="wrap" %}
```
windows: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=121c16ba1218dc3686b3cdac4705bc7496fb0fe7, for GNU/Linux 3.2.0, not stripped
```
{% endcode %}

```
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX enabled
    PIE:      PIE enabled
```

The program wants the user to input a password (flag). If the password incorrect, it will show this.

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

Checking the code using Ghidra, i can see that line 18 compares variable **local\_d** with array **arr**.

**local\_d** is the sum of the value at current index and the index after from user input.

`local_d = local_38[i+1] + local_38[i];`

<figure><img src="../../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

Double click the **arr\[**] to see the array.

```armasm
                             arr                                             XREF[3]:     Entry Point(*), main:0010119b(*), 
                                                                                          main:001011a2(*)  
        00104060 9c 96 bd        undefine
                 af 93 c3 
                 94 60 a2 
           00104060 9c              undefined19Ch                     [0]                               XREF[3]:     Entry Point(*), main:0010119b(*), 
                                                                                                                     main:001011a2(*)  
           00104061 96              undefined196h                     [1]
           00104062 bd              undefined1BDh                     [2]
           00104063 af              undefined1AFh                     [3]
           00104064 93              undefined193h                     [4]
           00104065 c3              undefined1C3h                     [5]
           00104066 94              undefined194h                     [6]
           00104067 60              undefined160h                     [7]
           00104068 a2              undefined1A2h                     [8]
           00104069 d1              undefined1D1h                     [9]
           0010406a c2              undefined1C2h                     [10]
           0010406b cf              undefined1CFh                     [11]
           0010406c 9c              undefined19Ch                     [12]
           0010406d a3              undefined1A3h                     [13]
           0010406e a6              undefined1A6h                     [14]
           0010406f 68              undefined168h                     [15]
           00104070 94              undefined194h                     [16]
           00104071 c1              undefined1C1h                     [17]
           00104072 d7              undefined1D7h                     [18]
           00104073 ac              undefined1ACh                     [19]
           00104074 96              undefined196h                     [20]
           00104075 93              undefined193h                     [21]
           00104076 93              undefined193h                     [22]
           00104077 d6              undefined1D6h                     [23]
           00104078 a8              undefined1A8h                     [24]
           00104079 9f              undefined19Fh                     [25]
           0010407a d2              undefined1D2h                     [26]
           0010407b 94              undefined194h                     [27]
           0010407c a7              undefined1A7h                     [28]
           0010407d d6              undefined1D6h                     [29]
           0010407e 8f              undefined18Fh                     [30]
           0010407f a0              undefined1A0h                     [31]
           00104080 a3              undefined1A3h                     [32]
           00104081 a1              undefined1A1h                     [33]
           00104082 a3              undefined1A3h                     [34]
           00104083 56              undefined156h                     [35]
           00104084 9e              undefined19Eh                     [36]

```

The value in each of the array is the value of **local\_d**, which i explained earlier. So, we need to calculate the value (in ascii) for the user input.

The flag format starts with **HTB{**. It should be easy for us to start calculate the rest of the value. You can use [ASCII Table](https://www.ascii-code.com/) as guidance and some simple math skills.

```
9C = H (48) + T (54)
96 = T (54) + B (42)
BD = B (42) + { (7B)
AF = { (7B) + 4 (34)
...
the rest of the calculations
...
9E = ! (21) + } (7D)
```

We get a flag from it, check it just to make sure it is legit.

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

***

### Flag

HTB{4\_d00r\_cl0s35\_bu7\_4\_w1nd0w\_0p3n5!}
