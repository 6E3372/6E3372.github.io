# betterthanu

***

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Solution

when running the program, we need to enter how many pp we got and type any last word.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

okay from this, i think i know what to do. So let's take a look at the source code.

<pre data-title="challenge.c" data-line-numbers><code>#include &#x3C;stdio.h>
#include &#x3C;string.h>
#include &#x3C;stdlib.h>
#include &#x3C;stdint.h>

FILE *flag_file;
char flag[100];

int main(void) {
<strong>    unsigned int pp;
</strong><strong>    unsigned long my_pp;
</strong><strong>    char buf[16];
</strong>
    setbuf(stdin, NULL);
    setbuf(stdout, NULL);

    printf("How much pp did you get? ");
    fgets(buf, 100, stdin);
    pp = atoi(buf);

<strong>    my_pp = pp + 1;
</strong>
    printf("Any last words?\n");
    fgets(buf, 100, stdin);

<strong>    if (pp &#x3C;= my_pp) {
</strong>        printf("Ha! I got %d\n", my_pp);
        printf("Maybe you'll beat me next time\n");
    } else {
        printf("What??? how did you beat me??\n");
        printf("Hmm... I'll consider giving you the flag\n");

<strong>        if (pp == 727) {
</strong>            printf("Wait, you got %d pp?\n", pp);
            printf("You can't possibly be an NPC! Here, have the flag: ");

            flag_file = fopen("flag.txt", "r");
            fgets(flag, sizeof(flag), flag_file);
            printf("%s\n", flag);
        } else {
            printf("Just kidding!\n");
        }
    }

    return 0;
}

</code></pre>

okay lets go line by line here.

<details>

<summary>Line 10, 11, 12</summary>

**unsigned int** has a max size of 4,294,967,295

**unsigned long** has a max size of 18,446,744,073,709,551,615

**char** have a size -127 to 127, but the size have been declared which is 16.

</details>

<details>

<summary>Line 21</summary>

the code indicates that `my_pp` will always `pp + 1`, each time we run the program

</details>

<details>

<summary>Line 26</summary>

this line checks for `pp` is smaller or equal to `my_pp`.

So, to bypass this checking, we must input a higher value for `pp` than `my_pp`

</details>

<details>

<summary>Line 33</summary>

Further in the if else statement, we can see that `if pp == 727`, we can get the flag.

</details>



Okay, so, now we know how the program works. We can do integer overflow for variable `pp`, but we cannot bypass the Line 33 statement.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

We must enter `pp` as 727 to get the flag. So i think it is not about integer flow, but we can do a buffer overflow on Line 23, which the program need as to input any word here.&#x20;



So, the pp will be 727, and "Any last words?" will be 16 bit of a's.



<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Flag

osu{i\_cant\_believe\_i\_saw\_it}
