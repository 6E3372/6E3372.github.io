---
description: shout out to Tryhackme for this interesting room!
---

# Intro

## :book: Threat hunting&#x20;

* is an approach to finding cyber security threats where there’s an active effort done to look for signs of malicious activity.
* basically we hunt/search for a threat in our environment
* it is contrast with Incident Response (IR)

|                  Reactive Approach                  |                         Proactive Approach                        |
| :-------------------------------------------------: | :---------------------------------------------------------------: |
|                  Incident Response                  |                           Threat Hunting                          |
|     Triggered by an initial notification / alert    | **Active search** for suspicious events that can become incidents |
|     Guided by the initial scope of the incident     |                   Guided by Threat Intelligence                   |
| "There's a threat that needs to be dealt with now." |         "There might be a threat that we don't know yet."         |

<figure><img src="../.gitbook/assets/image (9) (1).png" alt=""><figcaption></figcaption></figure>

***

## :notebook\_with\_decorative\_cover: Basis for Threat Hunting

* **Start with Accurate Leads:**
  * Utilize known relevant malware and trusted Threat Intelligence.
  * Leads provide better chances for success, from simple tasks to complex projects.
* **Threat Intelligence:**
  * Understand threats to predict their behavior within your environment.
  * Helps in narrowing down search to specific targets or tactics.
* **Unique Threat Intelligence:**
  * Internal intrusion experience allows for developing valuable intelligence.
  * Provides insights unique to your organization, such as Indicators of Compromise (IOCs).
* **Threat Intelligence Feeds:**
  * Access publicly available platforms like MISP for shared intelligence.
  * Invest in paid resources like Recorded Future or ReliaQuest for tailored intelligence.
  * Paid services offer extraordinary insights but come at a cost.

***

## :hushed: What do we hunt for?

|         General        | Example(s)                                                                                                                                                                |
| :--------------------: | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Known Relevant Malware | <ul><li><a href="https://github.com/ytisf/theZoo">theZoo</a></li><li><a href="https://www.trendmicro.com/vinfo/us/threat-encyclopedia/">Threat Encyclopedia</a></li></ul> |
|     Attack Residue     | <ul><li>Indicators of Attack (IOA)</li><li>Indicators of Compromise (IOC)</li></ul>                                                                                       |
|   Known Vulnerability  | <ul><li>0-day</li><li>CVE</li></ul>                                                                                                                                       |

***

## :thinking: How do we hunt for it?

### <mark style="color:red;">Attack Signatures and IOCs</mark>

* **Characterizing the Threat:**
  * Condense the identified threat into specific and actionable identifiers.
  * Facilitates immediate recognition of the threat during hunting.
* **Attack Signatures:**
  * Define patterns or behaviors indicative of the threat.
  * Helps in identifying relevant malware, attack residues, and exploited vulnerabilities.
* **Indicators of Compromise (IOCs):**
  * Specific pieces of data indicating malicious activity.
  * Include traces of the adversary's actions within the environment.
* **Comparing with Historical Data:**
  * Use Attack Signatures and IOCs to compare with available historical data.
  * Eases the process of finding objects of interest within the environment.
* **Understanding Environment Behavior:**
  * Knowledge of environment behavior aids in recognizing exploited vulnerabilities.
  * Understanding log patterns when vulnerabilities are exploited is crucial.

### <mark style="color:red;">**Logical Queries for Vulnerability Hunting**</mark>

* **Utilizing Logical Queries:**
  * Certain hunting projects benefit from logical queries for efficient results.
  * Example: Hunting for assets with known vulnerabilities.
* **Characterizing Vulnerable Assets:**
  * Define specific actionable identifiers for vulnerable assets (e.g., application version).
  * These identifiers facilitate crafting logical queries to filter for vulnerable assets.
* **Crafting Queries:**
  * Create queries that filter assets based on identified vulnerabilities.
  * Target low-hanging fruits for easy pickings while directly impacting the organization's security posture.
* **Efficient Impact:**
  * Logical queries streamline the hunting process, leading to efficient identification of vulnerable assets.
  * Addressing vulnerabilities promptly improves the organization's overall security posture.

### <mark style="color:red;">**Patterns of Activity in Threat Hunting:**</mark>

* **Characterizing Threat Behavior:**
  * After narrowing down specific threats (e.g., threat actors), focus shifts to characterizing their behavior.
  * Understanding patterns of activity aids in anticipating and detecting malicious actions.
* **MITRE ATT\&CK Matrix:**
  * Key resource for analyzing adversary tactics, techniques, and procedures (TTPs).
  * Provides a comprehensive framework for understanding and categorizing threat behaviors.
* **Utilizing MITRE ATT\&CK:**
  * Identify relevant techniques and procedures used by the threat actors.
  * Map observed behaviors to the corresponding entries in the ATT\&CK Matrix for classification and analysis.
* **Enhancing Detection Capabilities:**
  * By understanding common patterns of activity, detection capabilities can be enhanced.
  * Helps in proactively identifying and mitigating potential threats based on known TTPs.
* **Continuous Improvement:**
  * Regularly update and refine hunting strategies based on new insights and emerging threat trends.
  * MITRE ATT\&CK Matrix serves as a dynamic tool for ongoing threat intelligence and hunting efforts.

***

## :dart: Goals (or should i say why?)

* **Discover Pre-existing Bad:**
  * Malicious activities may evade detection mechanisms due to their complexity or chance.
  * Threat Hunting identifies such activities, triggering immediate Incident Response.
  * Learnings from hunts feed back into the continuous monitoring process of the Security Operations Center (SOC).
* **Minimize Dwell Time of Attackers:**
  * Undetected threat actor activity grants them a 'free pass' to explore the environment.
  * Longer dwell time increases the risk of sophisticated attacks and data theft.
  * Threat Hunting aims to minimize dwell time to mitigate potential damage to assets and data.
* **Develop Additional Detection Methods:**
  * Use findings from Threat Hunting to develop new detection mechanisms.
  * Continuous improvement ensures future threats are quickly detected and mitigated.
  * Translate threat profiles into actionable detection methods to enhance overall security posture.
