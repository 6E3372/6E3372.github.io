---
description: a simple guide on how to use the threat hunting tool
---

# FYP

## Guide

According to MITRE ATT\&CK Frameworks, there are a lot of TTP can be used by attacker.

Below are the description and what to search for.

***

### Reconnaissance

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

##
