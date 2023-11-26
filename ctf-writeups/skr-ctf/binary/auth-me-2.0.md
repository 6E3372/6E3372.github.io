# Auth Me 2.0

***

<figure><img src="../../../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

***

### Solution

Review the given c code

<pre class="language-c" data-title="auth_me2.c" data-line-numbers><code class="lang-c">#include &#x3C;stdio.h>
#include &#x3C;stdlib.h>
#include &#x3C;string.h>
#include &#x3C;signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void setup(){
  FILE *f = fopen("flag.txt","r");
  fgets(flag,FLAGSIZE_MAX,f);
  gid_t gid = getegid();
  setresgid(gid, gid, gid);
}

int main(int argc, char **argv){
  setup();
  char user[8];
  char pass[8];
  printf("Authenticate Me 2.0\n");
  printf("--------------------------------\n");
  printf("Enter your username: ");
  gets(user);
<strong>  if(strcmp(user,"admin") == 0){
</strong><strong>    printf("Don't pretent you're admin =(\n");
</strong><strong>    return 0;
</strong><strong>  }
</strong>  printf("Enter your password: ");
  gets(pass);
  if(strcmp(user,"admin") == 0 &#x26;&#x26; strcmp(pass,"admin") == 0){
    printf("Welcome admin! Here is your flag: %s",flag);
  }else if(strcmp(user,"user") == 0 &#x26;&#x26; strcmp(pass,"user") == 0){
    printf("Welcome %s! You're authenticated!\n");
  }else{
    printf("Invalid Username %s or Password %s\n",user,pass);
    printf("Hint: Distance between user and pass is %i\n",user-pass);
  }
  return 0;
}
</code></pre>

This challenge is similar to Auth Me 1, but it checks for username `admin` at line 25. We have given _**Tips: Press ctrl + shift + @ to enter null character.**_&#x20;

Now, i know that we must play with some null character that looks like this `\x00`. In C Language, program will stop reading until it finds a null character. We cannot input `admin\x00` as the program will read it as string.

<figure><img src="../../../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

Btw, the program give us a hint that the distance between variable `user` and `pass` is **8**. So, i try to overflow the variable `user` with 8 bytes like this `admin\x00\x00\x00` <- \x00 is 1 byte ya.

This is the python one line command that i figure out.

```bash
python3 -c "print('\nadmin'+('\x00' * 3)+'admin')" | ./auth2
```

Using that, we can get the flag :checkered\_flag:

<figure><img src="../../../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

***

### Flag

SKR{C\_St0p\_rE4dinG\_untIL\_nuLL\_4b4b8e}
