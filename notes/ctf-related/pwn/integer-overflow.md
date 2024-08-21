# Integer Overflow

**Definition :** Overflow the limitation of a program with an integer.&#x20;

## Limitations On Integers in C

In any language, not only C, have its own [variable type](#user-content-fn-1)[^1] and [type modifiers](#user-content-fn-2)[^2]. It has it's own limitation value. However, in can be limited by the program itself.

<table><thead><tr><th align="center">Min</th><th width="270" align="center">Variable Type / Type Modifiers</th><th align="center">Max</th></tr></thead><tbody><tr><td align="center">-32,768 bits</td><td align="center">short</td><td align="center">32,767 bits</td></tr><tr><td align="center">-2,147,483,648</td><td align="center">int</td><td align="center">2,147,483,647</td></tr><tr><td align="center">-9,223,372,036,854,775,808 bits</td><td align="center">long</td><td align="center">9,223,372,036,854,775,807 bits</td></tr><tr><td align="center">0</td><td align="center">unsigned short int </td><td align="center">65,535</td></tr><tr><td align="center">0</td><td align="center">unsigned int </td><td align="center">4,294,967,295</td></tr><tr><td align="center">-128</td><td align="center">signed char </td><td align="center">127</td></tr><tr><td align="center">0</td><td align="center">unsigned char</td><td align="center">255</td></tr></tbody></table>



<img src="../../../.gitbook/assets/file.excalidraw (1).svg" alt="This image hopefully helps you to understand the explaination below" class="gitbook-drawing">

For a better understanding on how it works, look at your analog clock. The clock has a limit of 12 numbers only. Let say the time right now is 9 am. In 12 hours, the clocks points back at number 9 but in pm. It does not point at number 21 right? Yeah that's how i understanding the limitations (i know it does not make sense, but why not :rofl:)

## Tips :clipboard:

1. Knowing the limitation of the variable type is a must
2. Try to input something so that the variable will exceed the limit
3. \--

[^1]: char, int, float, double etc..

[^2]: signed, unsigned, short, long
