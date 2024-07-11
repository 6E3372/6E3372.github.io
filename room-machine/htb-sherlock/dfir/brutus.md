# Brutus

<figure><img src="../../../.gitbook/assets/image (97).png" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (98).png" alt=""><figcaption></figcaption></figure>

***

## Task 1

> Analyzing the auth.log, can you identify the IP address used by the attacker to carry out a brute force attack?

The provided auth.log shows that **65.2.161.68** is the IP address that performed the bruteforce attack.

It is because many failed login attempt within several seconds coming from that IP which indicate that the attacker is brute forcing login credentials.

<figure><img src="../../../.gitbook/assets/image (99).png" alt=""><figcaption></figcaption></figure>

***

## Task 2

> The brute force attempts were successful, and the attacker gained access to an account on the server. What is the username of this account?

Following the brute force progress, there is only one accepted login which is for username **root**, then it immediately disconnect, meaning that probably the brute force scripts are trying to finish the rest of the password list.

<figure><img src="../../../.gitbook/assets/image (100).png" alt=""><figcaption></figcaption></figure>

***

## Task 3

> Can you identify the timestamp when the attacker manually logged in to the server to carry out their objectives?

Of course after the brute forcing process is done, the attacker try to login with the valid credentials manually.

Here are the first manual login attempt by the attacker. Take this part and relate it with the wtmp file given to get the exact timestamp the attacker logged in as root.

<figure><img src="../../../.gitbook/assets/image (101).png" alt=""><figcaption></figcaption></figure>

Using tools like utmpdump, we can dump the wtmp files and see all the details.&#x20;

The line highlighted on the picture below is related with picture above.&#x20;

We can see the same IP address login at a similar timestamp

The answer for task 3 is **2024-03-06 06:32:45**

<figure><img src="../../../.gitbook/assets/image (103).png" alt=""><figcaption></figcaption></figure>

***

## Task 4

> SSH login sessions are tracked and assigned a session number upon login. What is the session number assigned to the attacker's session for the user account from Question 2?

After any successful login, a session number will be assigned. Looking at the picture below, the user root logged in by the attacker being assigned as session number **37**

<figure><img src="../../../.gitbook/assets/image (104).png" alt=""><figcaption></figcaption></figure>

***

## Task 5

> The attacker added a new user as part of their persistence strategy on the server and gave this new user account higher privileges. What is the name of this account?

Right after the attacker login manually, the attacker created a new user named **cyberjunkie** and give a high privilege to it by adding the user to the sudo group

<figure><img src="../../../.gitbook/assets/image (105).png" alt=""><figcaption></figcaption></figure>

***

## Task 6

> What is the MITRE ATT\&CK sub-technique ID used for persistence?

Understand what the attacker is doing, we can conclude that the attacker is using T1136.001 for the attack.

Referrence: [https://attack.mitre.org/techniques/T1136/001/](https://attack.mitre.org/techniques/T1136/001/)

***

## Task 7

> How long did the attacker's first SSH session last based on the previously confirmed authentication time and session ending within the auth.log? (seconds)

The session last for **279** seconds based on the findings in the auht.log.

We can easily use the command `strings auth.log | grep root` to only filter out the logs related to root&#x20;

<figure><img src="../../../.gitbook/assets/image (106).png" alt=""><figcaption></figcaption></figure>

***

## Task 8

> The attacker logged into their backdoor account and utilized their higher privileges to download a script. What is the full command executed using sudo?

To search for command executed in auth.log, we can use command **strings auth.log | grep COMMAND** to filter it out.

Here, there is a curl command executed to receive data from  **https://raw.githubusercontent.com/montysecurity/linper/main/linper.sh**

<figure><img src="../../../.gitbook/assets/image (107).png" alt=""><figcaption></figcaption></figure>
