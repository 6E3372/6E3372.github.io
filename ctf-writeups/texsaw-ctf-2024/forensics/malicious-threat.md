# Malicious Threat

<figure><img src="../../../.gitbook/assets/image (12) (1).png" alt=""><figcaption></figcaption></figure>

***

## Solution

Given a .txt file that contains a web server log.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Upon analysis, we there were important directories that have been access such as **/login** and **/admin**.

Filtering out these directories using `cat logs.txt | grep /admin` give as a list of **/admin** directories and sub directory being access.

What interesting is there are only one sub directory that we are aware of is accessibility on the internet

<figure><img src="../../../.gitbook/assets/image (3) (1) (1) (1).png" alt=""><figcaption><p>/ufile.io/y8ls94tu</p></figcaption></figure>

Enter the link in the browser redirect us to an online file uploader named ufile.io

<figure><img src="../../../.gitbook/assets/image (5) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Download the given file (Admin.zip) and analyse it.

Filter out the flag prefix and it's done and dusted.

<figure><img src="../../../.gitbook/assets/image (6) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Flag

texsaw{g0tcha\_fl@g\_m1ne}
