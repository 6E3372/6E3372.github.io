# Lost Some Magic

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Solution

p/s: this challenge is more to forensics imo.

Given a **data** file to get started. Based on the challenge description, it mentions about **magic** and **compressed**.

**Magic** - Magic Number / Header File Signature that determine the type of file

**Compressed** - compressed file like .zip, .tar etc..

Basically, we need to change the file header signature to revert to the original file.

<figure><img src="../../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption><p>file signature for data file</p></figcaption></figure>

As we can see from the picture above, the starting byte for the file header signature is **B** or **42** in hex.

Looking up for a cheat sheet [here](https://en.wikipedia.org/wiki/List\_of\_file\_signatures), i know that compressed files that start with that bytes is **bzip** with a file header of **BZh (42 5A 68)**. So, edit the byte and we got the original bzip file.

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Upon extracting that file, we retrieve another corrupt file which i named it datafixed2.

<figure><img src="../../../.gitbook/assets/image (4) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Again, looking at its signature file, we can see something interesting.

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Here, i can see a string of **ust** which may be a header file for another compressed file. Based on the **file** command, i know that this file is a corrupted tar archive file. So, just edit the file signature at 00000100 to **ustar␠␠␀ (75 73 74 61 72 20 20 00)**. After that we got the original tar archive file.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Upon extracting it, we got another compressed file.

<figure><img src="../../../.gitbook/assets/image (7) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

From here, there's nothing much. Just extract it and we got a **.txt** file for flag

<figure><img src="../../../.gitbook/assets/image (8) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Flag

swampCTF{C0113ct1ng\_th3\_mag1c\_number5}
