# Admin Rights

<figure><img src="../../../.gitbook/assets/image (8) (1).png" alt=""><figcaption></figcaption></figure>

***

### Solution

File given is a windows registry file

<figure><img src="../../../.gitbook/assets/image (10) (1).png" alt=""><figcaption></figcaption></figure>

For this challenge, i use `chntpw` to list out all the user and its role with command `chntpw -l <filename>`&#x20;

We can see that user\_7565 has the role admin.

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

***

### Flag

grodno{user\_7565}
