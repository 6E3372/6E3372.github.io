# Jingle Bell

<figure><img src="../../../.gitbook/assets/image (1).png" alt="" width="188"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

***

## Setting Up

1. Install SQLite DB Browser -> [https://sqlitebrowser.org/dl/](https://sqlitebrowser.org/dl/)
2. Open Database -> Choose wpndatabase.db -> Click "Browse Data" Tab -> Choose "Notification" Table

***

## Task 1

> Which software/application did Torrin use to leak Forela's secrets?

Upon analysing the database, there were rows that were tagged with "toast". The application used in this communication can be seen in the payload section. Which is [slack](https://slack.com/).&#x20;

<figure><img src="../../../.gitbook/assets/image (2).png" alt="" width="443"><figcaption></figcaption></figure>

***

## Task 2

> What's the name of the rival company to which Torrin leaked the data?

Just right below the answer in Task 1, there was a title given, which probably the rival company that Torrin leaked the data to.

<figure><img src="../../../.gitbook/assets/image (3).png" alt="" width="444"><figcaption></figcaption></figure>

***

## Task 3

> What is the username of the person from the competitor organization whom Torrin shared information with?

Checking the next row suggest that **Cyberjunkie-PrimeTechDev** accepted an invitation from Torrin. The user was the person who, Torrin shared the information with.

<figure><img src="../../../.gitbook/assets/image (5).png" alt="" width="443"><figcaption></figcaption></figure>

***

## Task 4

> What's the channel name in which they conversed with each other?

The next row in the database shows the conversation between them in a channel called **forela-secrets-leak**

<figure><img src="../../../.gitbook/assets/image (6).png" alt="" width="440"><figcaption></figcaption></figure>

***

## Task 5

> What was the password for the archive server?

Then, the user give Torrin the password for the archive server, which is **Tobdaf8Qip$re@1**

<figure><img src="../../../.gitbook/assets/image (7).png" alt="" width="440"><figcaption></figcaption></figure>

***

## Task 6

> What was the URL provided to Torrin to upload stolen data to?

Reading the next conversation reveals the URL for Torrin to upload the data.

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

***

## Task 7

> When was the above link shared with Torrin?

In the same message the user send the link, there was a Unix timestamp declared above it. Take the value and convert it to UTC.

<figure><img src="../../../.gitbook/assets/image (9).png" alt="" width="444"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (10).png" alt="" width="563"><figcaption></figcaption></figure>

***

## Task 8

> For how much money did Torrin leak Forela's secrets?

Last conversation between them was a deal promised for Torrin which about £10000 :money\_mouth:

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption></figcaption></figure>
