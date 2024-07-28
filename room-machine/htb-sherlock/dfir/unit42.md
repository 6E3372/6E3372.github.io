# Unit42

<figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 1

> How many Event logs are there with Event ID 11?

Filter out the event that have event ID 11, we a total number of **56**.

<figure><img src="../../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 2

> Whenever a process is created in memory, an event with Event ID 1 is recorded with details such as command line, hashes, process path, parent process path, etc. This information is very useful for an analyst because it allows us to see all programs executed on a system, which means we can spot any malicious processes being executed. What is the malicious process that infected the victim's system?

Analyzing event ID 1, we can see there are one file that is named suspiciously which is **C:\Users\CyberJunkie\Downloads\Preventivo24.02.14.exe.exe**

<figure><img src="../../../.gitbook/assets/image (3) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 3

> Which Cloud drive was used to distribute the malware?

Looking at the timestamp of the malicious file, we search for event ID 22 that is responsible for DNS queries happening in the system.&#x20;

We can assume that the attacker used **DropBox** to distribute the malware.

<figure><img src="../../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 4

> The initial malicious file time-stamped (a defense evasion technique, where the file creation date is changed to make it appear old) many files it created on disk. What was the timestamp changed to for a PDF file?

Find the keyword PDF, we can see that the file time creation is changed from 2024-02-14 03:41:58 to **2024-01-14 08:10:06** .

<figure><img src="../../../.gitbook/assets/image (5) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 5

> The malicious file dropped a few files on disk. Where was "once.cmd" created on disk? Please answer with the full path along with the filename.

Filter out once.cmd, we can see the full path of the file. Which also we can conclude that this file is related to the malicious process we found earlier.

<figure><img src="../../../.gitbook/assets/image (6) (1).png" alt=""><figcaption></figcaption></figure>

***

## Task 6

> The malicious file attempted to reach a dummy domain, most likely to check the internet connection status. What domain name did it try to connect to?

Looking at bottom of the logs, we can see that the malicious process it trying to connect with a domain name which is **www.example.com** .

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

***

## Task 7

> Which IP address did the malicious process try to reach out to?

Looking up at event ID 3, we can found the destination IP address that the system trying to reach out, which is **93.184.216.34**

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

***

## Task 8

> The malicious process terminated itself after infecting the PC with a backdoored variant of UltraVNC. When did the process terminate itself?

Looking at event ID 5, the malicious process terminate itself at **2024-02-14 03:41:58**

<figure><img src="../../../.gitbook/assets/image (9).png" alt=""><figcaption></figcaption></figure>

