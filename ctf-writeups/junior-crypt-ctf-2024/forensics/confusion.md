# Confusion

<figure><img src="../../../.gitbook/assets/image (87).png" alt=""><figcaption></figcaption></figure>

***

### Solution

Given a microsoft word file

<figure><img src="../../../.gitbook/assets/image (88).png" alt=""><figcaption></figcaption></figure>

Upon extracting the file using binwalk, there are some folders to be investigate further.

<figure><img src="../../../.gitbook/assets/image (89).png" alt=""><figcaption></figcaption></figure>

In **docProps** directory there open the **core.xml** file, there is a base64 of a file that need to be retrieve.

<figure><img src="../../../.gitbook/assets/image (90).png" alt=""><figcaption></figcaption></figure>

We can retrieve the file by inputting the base64 encoding in cyberchef

<figure><img src="../../../.gitbook/assets/image (91).png" alt=""><figcaption></figcaption></figure>

We then get a **.rar** file.

<figure><img src="../../../.gitbook/assets/image (92).png" alt=""><figcaption></figcaption></figure>

The archive file is being protected by a password

<figure><img src="../../../.gitbook/assets/image (93).png" alt=""><figcaption></figcaption></figure>

We then crack the password using hashcat.

The steps are as below

1. Convert the RAR file to hash\
   `rar2john download.rar > key.hash`
2. Delete `download.rar:` at the beginning of the hash \
   (Result: $rar5$16$35e8bb91e14c285f591003fe186c98a1$15$39870592e030495d2c766f945d14ccb8$8$215f837b53e3d0fd)
3. Crack the hash! \
   `hashcat -a 3 key.hash ?d?d?d?d`
4. Run again hash with --show flag to display the cracked password\
   `hashcat -a 3 key.hash ?d?d?d?d --show`

<figure><img src="../../../.gitbook/assets/image (94).png" alt=""><figcaption></figcaption></figure>

{% hint style="info" %}
yup for the ?d?d?d?d need a bit of guessing
{% endhint %}



Next enter the cracked password to retrieve a text file which contains a flag.

<figure><img src="../../../.gitbook/assets/image (95).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (96).png" alt=""><figcaption></figcaption></figure>

***

### Flag

grodno{ctf\_zip\_key}
