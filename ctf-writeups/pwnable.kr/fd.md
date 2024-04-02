# fd

<figure><img src="../../.gitbook/assets/image (78).png" alt=""><figcaption></figcaption></figure>

***

## Solution

Given a C file. Let's do some basic checking on it.

<figure><img src="../../.gitbook/assets/image (80).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (79).png" alt=""><figcaption></figcaption></figure>

<pre class="language-c" data-title="fd.c" data-line-numbers><code class="lang-c">#include &#x3C;stdio.h>
#include &#x3C;stdlib.h>
#include &#x3C;string.h>
char buf[32];
int main(int argc, char* argv[], char* envp[]){
        if(argc&#x3C;2){
                printf("pass argv[1] a number\n");
                return 0;
        }
<strong>        int fd = atoi( argv[1] ) - 0x1234;
</strong>        int len = 0;
        len = read(fd, buf, 32);
<strong>        if(!strcmp("LETMEWIN\n", buf)){
</strong>                printf("good job :)\n");
                system("/bin/cat flag");
                exit(0);
        }
        printf("learn about Linux file IO\n");
        return 0;

}
</code></pre>

Based on the source code given, we can see there are 2 lines that are very interesting.

<details>

<summary>Line 10</summary>

* `atoi()` function in C converts a string to an integer
* it takes `argv[1]` as its argument and substract it with **0x1234** which is **4660** in decimal
* the result is stored in variable `fd`

</details>

<details>

<summary>Line 13</summary>

* it compares a strings in variable `buf` with "LETMEWIN\n"
* that's it

</details>

Between the lines, we can see there is a `read()` function which takes file descriptor, some buffer and number of bytes. We need to make the **file descriptor equals 0** so that we can write a string to the program and pass the **if statement** in Line 13.

So we input **4660** which then it will substract with 0x1234 and returns 0. Then write **LETMEWIN** to the program.

<figure><img src="../../.gitbook/assets/image (81).png" alt=""><figcaption></figcaption></figure>

Yeah. Nice challenge btw :thumbsup:

***

## Flag

mommy! I think I know what a file descriptor is!!
