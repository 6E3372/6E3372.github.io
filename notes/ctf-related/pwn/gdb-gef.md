# gdb-gef

## Commands

* Run the program
  * r
* Continue the program
  * c

### Breakpoints

| Command     | Explaination                                               |
| ----------- | ---------------------------------------------------------- |
| b \*main+25 | setup a breakpoint at **main** function line number **25** |
| b \*calc    | setup a breakpoint at **calc** function                    |
| del 2       | delete breakpoint numbered **2**                           |

### Viewing Things

| Command        | Explaination                                              |
| -------------- | --------------------------------------------------------- |
| info b         | show all breakpoints                                      |
| info registers | show registers                                            |
| info frame     | show stack frame                                          |
| disass main    | look at **main** function / disassamble **main** function |
| info func      | show all functions                                        |
|                |                                                           |
