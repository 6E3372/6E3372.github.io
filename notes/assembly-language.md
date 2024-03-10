# Assembly Language

* Assembly is a low-level programming language used to directly translate instructions into the computer’s machine code in a more human-readable way.

***

## Spesific Use Case

* Embedded systems that have limited memory and hardware capacity
* Direct hardware testing
* Software optimization

***

## Compilation Process

1. Preprocessing - prepare the user’s code for machine code by removing comments, expanding included macros, and performing any code maintenance prior to handing the file to the compiler.
2. Compiling - the process of taking the expanded file from the preprocessor and translating the program into an optimized Assembly language.
3. Assembling - process of taking an assembly language program and using an assembler to generate machine code.
4. Linking - process of filling in function calls, including additional objects, libraries, and source code from other locations into the main source code.

***

## ARM Arithmethic Operations Opcode

| Instruction | Function                                                                                             | Example       | Explaination                                          |
| ----------- | ---------------------------------------------------------------------------------------------------- | ------------- | ----------------------------------------------------- |
| ADD         | adding numbers                                                                                       | ADD a, b, c   | <ul><li>adding value b and c, stored in a</li></ul>   |
| ADDI        | adding immidiate number (constant value) rather than being fetched from registers or memory location | ADDI a, c, 10 | <ul><li>adding 10 to a, and stored in c</li></ul>     |
| SUB         | substracting number                                                                                  | SUB a, b, c   | <ul><li>substract value and c, stored in a</li></ul>  |
| MUL         | multiply number                                                                                      | MUL a, b, c   | <ul><li>multiply value b and c, stored in a</li></ul> |

***

## Bitwise Logic Operations

{% hint style="info" %}
Syntax

{instruction} {destination}, {source1}, {source2}
{% endhint %}

| Instruction | Example     | Comparison in C | Explaination                                                     |
| ----------- | ----------- | --------------- | ---------------------------------------------------------------- |
| AND         | AND a, b, c | a = b && c      | <ul><li>result of b AND c, stored in a</li></ul>                 |
| ORR         | ORR a, b, c | a = b \|\| c    | <ul><li>result of b OR c, stored in a</li></ul>                  |
| EOR         | EOR a, b, c | a = b ^ c       | <ul><li>result of b XOR c, stored in c</li></ul>                 |
| BIC         | BIC a, b, c | a = b & (!c)    | <ul><li>the result of b AND negation of c, stored in a</li></ul> |

***

## Others

| Instruction | Example  | Comparison in C | Explaination                                |
| ----------- | -------- | --------------- | ------------------------------------------- |
| CMP         | CMP a, b | a == b          | <ul><li>compares value at a and b</li></ul> |
| MOV         | MOV a, 1 | a = 1           | <ul><li>assign value 1 to a</li></ul>       |
|             |          |                 |                                             |
