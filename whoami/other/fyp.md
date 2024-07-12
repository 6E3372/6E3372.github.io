---
description: a simple guide on how to use the threat hunting tool
---

# FYP

## Guide

According to MITRE ATT\&CK Frameworks, there are a lot of TTP can be used by attacker.

Below are the description and what to search for.

***

### Reconnaissance - TA0043

<details>

<summary>T1595.001</summary>

**Name:** Scanning IP blocks

**Description:** Attacker scanning victim's IP block to gather network information.



**Data Source:** Access Log

**Keyword:** nmap



Reference: [https://attack.mitre.org/techniques/T1595/001/](https://attack.mitre.org/techniques/T1595/001/)

</details>

<details>

<summary>T1595.002</summary>

**Name:** Vulnerability Scanning

**Description:** Attacker may scan victim for known or unknown vulnerability to exploit



**Data Source:** Access Log

**Keyword:** nmap



Reference: [https://attack.mitre.org/techniques/T1595/002/](https://attack.mitre.org/techniques/T1595/002/)

</details>

<details>

<summary>T1595.003</summary>

**Name:** Wordlist Scanning

**Description:** Attacker may use brute forcing or crawling technique to understand the victim's infrastructure



**Data Source:** Access Log

**Keyword:** gobuster, dirbuster



Reference: [https://attack.mitre.org/techniques/T1595/003/](https://attack.mitre.org/techniques/T1595/003/)

</details>

***

### Initial Access - TA0001

<details>

<summary>T1133</summary>

**Name:** External Remote Services

**Description:** Adversaries may leverage external-facing remote services to initially access and/or persist within a network



**Data Source:** Auth Log

**Keyword:** ssh, sshd



Reference: [https://attack.mitre.org/techniques/T1133/](https://attack.mitre.org/techniques/T1133/)

</details>

#### Valid Accounts - T1078 <a href="#undefined" id="undefined"></a>

<details>

<summary>T1078.003</summary>

**Name:** Local Accounts

**Description:** Adversaries may obtain and abuse credentials of a local account



**Data Source:** Auth Log

**Keyword:** failed, Failed, Accept, Accepted, accept, accepted



**Reference:** [https://attack.mitre.org/techniques/T1078/](https://attack.mitre.org/techniques/T1078/)

</details>

***

### Execution - TA0002

#### Command and Scripting Interpreter - T1059 <a href="#undefined" id="undefined"></a>

<details>

<summary>T1059.004</summary>

**Name:** Unix Shell

**Description:** Adversaries may abuse Unix shell commands and scripts for execution



**Data Source:** Auth Log

**Keyword:** COMMAND



**Data Source:** Command History

**Keyword:** \<anything>



Reference: [https://attack.mitre.org/techniques/T1059/004/](https://attack.mitre.org/techniques/T1059/004/)

</details>

#### Scheduled Task/Job - T1053 <a href="#undefined" id="undefined"></a>

<details>

<summary>T1053.003</summary>

Name: Cron

Description: Adversaries may abuse the `cron` utility to perform task scheduling for initial or recurring execution of malicious code



Data Source: Auth Log, Syslog

Keyword: CRON



Reference: [https://attack.mitre.org/techniques/T1053/003/](https://attack.mitre.org/techniques/T1053/003/)

</details>

***

### Persistence - TA0003

#### Create Account - T1136 <a href="#undefined" id="undefined"></a>

<details>

<summary>T1136.001</summary>

Name: Local Account

Description: Adversaries may create a local account to maintain access to victim systems



Data Source: Auth Log

Keyword: useradd, usermod



Reference: [https://attack.mitre.org/techniques/T1136/001/](https://attack.mitre.org/techniques/T1136/001/)

</details>

***

### Privilege Escalation - TA0004

#### Abuse Elevation Control Mechanism - T1548 <a href="#undefined" id="undefined"></a>

<details>

<summary>T1548.003</summary>

Name: Sudo and Sudo Caching

Description: Adversaries may perform sudo caching and/or use the sudoers file to elevate privileges



Data Source: Auth Log

Keyword: sudo



Reference: [https://attack.mitre.org/techniques/T1548/003/](https://attack.mitre.org/techniques/T1548/003/)

</details>



***

### Credential Access - TA0006

#### Brute Force - T1110

<details>

<summary>T1110.001, T1110.002, T1110.003, T1110.004</summary>

Name: Password Guessing, Password Cracking, Password Spraying, Credential Stuffing

Description: Adversaries may use brute force techniques to gain access to accounts when passwords are unknown or when password hashes are obtained



Data Source: Auth Log

Keyword: Failed password, password



Reference: [https://attack.mitre.org/techniques/T1110/](https://attack.mitre.org/techniques/T1110/)

</details>
