---
layout:
  title:
    visible: true
  description:
    visible: false
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# pwn

* Basically pwn (Binary Exploitation) is one of the CTF category that needs you to play with the binary of a code. Mostly it will be a C language or ELF, but don't be suprise if the challenge give you other than that

## Basic Checking

|             Command            | Explaination                                      |
| :----------------------------: | ------------------------------------------------- |
|         file `filename`        | to know what file type is the file                |
|       strings `filename`       | print all printable strings                       |
|       checksec `filename`      | check the properties of an executable             |
|        strace `filename`       | trace system calls and signals                    |
| objdump -M intel -d `filename` | displaying various information about object files |

{% content-ref url="format-string-vulnerability.md" %}
[format-string-vulnerability.md](format-string-vulnerability.md)
{% endcontent-ref %}

{% content-ref url="integer-overflow.md" %}
[integer-overflow.md](integer-overflow.md)
{% endcontent-ref %}

{% content-ref url="executable-properties.md" %}
[executable-properties.md](executable-properties.md)
{% endcontent-ref %}

{% content-ref url="gdb-gef.md" %}
[gdb-gef.md](gdb-gef.md)
{% endcontent-ref %}
