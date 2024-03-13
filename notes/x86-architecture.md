---
description: from Malware analysis pov, thanks to Tryhackme for this room
---

# x86 Architecture

**Control Unit**

* gets instructions from the main memory, depicted here outside the CPU
* next instruction to execute is stored in IP[^1] (x86), EIP (x32), RIP (x64)
* **Arithmetic Logic Unit (ALU)**
  * executes the instruction fetched from the Memory
  * results then stored in either the Registers or the Memory
* **Registers**
  * CPU's storage
* **Memory**
  * Main Memory or Random Access Memory (RAM)
  * contains all the code and data for a program to run
* **I/O Device**
  * all other devices that interact with a computer

***

## Registers

<details>

<summary>Instruction Pointer</summary>

* also known as Program Counter
* register that contains the address of the next instruction to be executed by the CPU
* IP[^2] in x86, EIP[^3] in x32, RIP[^4] in x64

</details>

### General-Purpose Registers

* In x86 system, general-purpose registers are all in 32-bits registers
* used during the general execution of instructions by the CPU
* In 64-bit systems, these registers are extended as 64-bit registers

<figure><img src="../.gitbook/assets/image (64).png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="Accumulator" %}
* Store results of arithmetic operations
* RAX (64-bits)
* EAX (32-bits)
* AX (16-bits)
* AH (Higher 8-bits)
* AL (Lower 8-bits)
{% endtab %}

{% tab title="Base" %}
* used to store the Base address for referencing an offset
* RBX (64-bits)
* EBX (32-bits)
* BX (16-bits)
* BH (Higher 8-bits)
* BL (Lower 8-bits)
{% endtab %}

{% tab title="Counter" %}
* used in counting operations such as loops, etc
* RCX (64-bits)
* ECX (32-bits)
* CX (16-bits)
* CH (Higher 8-bits)
* CL (Lower 8-bits)
{% endtab %}

{% tab title="Data" %}
* used in multiplication/division operations
* RDX (64-bits)
* EDX (32-bits)
* DX (16-bits)
* DH (Higher 8-bits)
* DL (Lower 8-bits)
{% endtab %}

{% tab title="Stack Pointer" %}
* It points to the top of the stack and is used in conjunction with the Stack Segment register
* RSP (64-bits)
* ESP (32-bits)
{% endtab %}

{% tab title="Base Pointer" %}
* used to access parameters passed by the stack
* it is used in conjunction with the Stack Segment register
* RBP (64-bits)
* ESP (32-bits)
{% endtab %}

{% tab title="Source Index" %}
* used for string operations
* It is used with the Data Segment (DS) register as an offset
* RSI (64-bits)
* ESI (32-bits)
{% endtab %}

{% tab title="Destination Index" %}
* It is used for string operations
* It is used with the Extra Segment (ES) register as an offset
* RDI (64-bits)
* EDI (32-bits)
{% endtab %}
{% endtabs %}

### Status Flag Registers

* provide indication about the status of the execution
* RFLAGS (64-bits) or EFLAGS (32-bits)
* The status flags register consists of individual single-bit flags that can be either 1 or 0

{% tabs %}
{% tab title="Zero Flag" %}
* ZF
* indicates when the result of the last executed instruction was zero
* For example, if an instruction is executed that subtracts a RAX from itself, the result will be 0. In this situation, the ZF will be set to 1.
{% endtab %}

{% tab title="Carry Flag" %}
* CF
* indicates when the last executed instruction resulted in a number too big or too small for the destination
* For example, if we add 0xFFFFFFFF and 0x00000001 and store the result in a 64-bit register, the result will be too big for the register. In this case, CF will be set to 1.
{% endtab %}

{% tab title="Sign Flag" %}
* SF
* indicates if the result of an operation is negative or the most significant bit is set to 1
{% endtab %}

{% tab title="Trap Flag" %}
* TF
* indicates if the processor is in debugging mode
* When the TF is set, the CPU will execute one instruction at a time for debugging purposes.
{% endtab %}

{% tab title="Fake Flag" %}

{% endtab %}
{% endtabs %}

### Segment Registers

* convert the flat memory space into different segments for easier addressing
* **Code Segment**
  * CS
  * points to the Code section in the memory
* **Data Segment**
  * DS
  * points to the program's data section in the memory
* **Stack Segment**
  * SS
  * points to the program's Stack in the memory
* **Extra Segments**
  * ES, FS, and GS
  * These extra segment registers point to different data sections. These and the DS register divide the program's memory into four distinct data sections.&#x20;

***



[^1]: Instruction Pointer

[^2]: Instruction Pointer

[^3]: Extended Instruction Pointer

[^4]: Register Instruction Pointer
