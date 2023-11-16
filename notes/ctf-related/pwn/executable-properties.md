# Executable Properties

When you run checksec, this will show

```bash
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX enabled
    PIE:      PIE enabled
```

{% tabs %}
{% tab title="RelRO" %}
Relocation Read-Only

**Definition :** This feature controls the permissions of the relocation table

* Full RELRO - ensures that the relocation table is read-only after the program starts
* Partial RELRO - some parts of the relocation table are still writable

```bash
//To Enable Full
gcc -o filename filename.c -Wl,-z,relro,-z,now

//To Enable Partial
gcc -o filename filename.c -Wl,-z,relro

//To Disable
gcc -o filename filename.c
```
{% endtab %}

{% tab title="Stack" %}
Canary Value

**Definition :** is a random value placed on the stack before the return address. it helps detect buffer overflows by checking whether the canary value has been altered.

* Canary found
* No canary found

```bash
//To Enable
gcc -o filename filename.c -fstack-protector

//To Disable
gcc -o filename filename.c -fno-stack-protector
```
{% endtab %}

{% tab title="NX" %}
No eXecute

**Definition :** This feature marks sections of memory as non-executable, preventing the execution of code in those regions

* NX enabled - preventing the execution of code on the stack
* NX disabled - can execute code on the stack

```bash
//To Enable
gcc -o filename filename.c -z noexecstack

//To Disable
gcc -o filename filename.c -z execstack
```
{% endtab %}

{% tab title="PIE" %}
Position Independent Executable

**Definition :** enables the randomization of the base address of the executable and its libraries, making it more difficult for attackers to predict the location of specific functions or gadgets in memory

* PIE enabled - the binary can be loaded at different addresses in memory each time the program is executed&#x20;
* No PIE - the binary is not Position Independent, and its base address is fixed

```bash
//To Enable
gcc -o filename filename.c -fPIE -pie

//To Disable
gcc -o filename filename.c
```
{% endtab %}
{% endtabs %}



