# Common Tactics

There are a bunch of tactics we can found in [MITRE ATT\&CK Frameworks](https://attack.mitre.org/). The following are some of the examples.



{% tabs %}
{% tab title="Initial Access" %}
* Initial Access Tactic (TA0001)
* techniques and strategies to breach an organisation
* focus on delivering payload to target system or network

### Objective

* to gain a foothold in the network

### Examples

* Social Engineering techniques such as phishing.
* Exploiting vulnerabilities through public-facing servers.
* Spraying credentials through exposed authentication endpoints.
* Executing commands through malicious flash drives.
* Installing cracked software with hidden malicious code.

### Access gained

* account access via valid credentials
* machine access via RCE

### What to hunt?

* intrusion attempts
* signs of method mentioned above
{% endtab %}

{% tab title="Execution" %}
* Execution Tactic (TA0002)
* execute or run their malicious code in conjunction with the initial access techniques or ways of delivering the attack.
* it enables the attackers to successfully run their commands remotely and continue with the series of attacks to establish further access.

### Examples

* Execution through command-line tools like PowerShell and Windows Command Processor (cmd.exe).
* Execution through built-in system tools or using [Living-off-the-land Binaries (LOLBAS)](https://lolbas-project.github.io/).
* Execution through scripting/programming tools, such as Python or PHP.

### What to hunt?

* Unusual process creation
* network connections
* file modifications
* etc.
{% endtab %}

{% tab title="Defense Evasion" %}
* Defense Evasion Tactic (TA0005)
* disguising malicious activities as usual legitimate operations or manipulating known benign files or processes

### Objective

* to avoid detection by network security systems during or following an infiltration.

### Examples

* Disabling security software.
* Deleting attack footprints on logs.
* Deceiving analysts through masquerading, obfuscation, and encryption.&#x20;
* Executing known bypasses to security controls.

### What to hunt?

* traces in logs
{% endtab %}

{% tab title="Persistence" %}
* Persistence Tactic (TA0003)

### Objective

* to maintain access to a compromised network over an extended period

### Examples

* Modification of registry keys to hijack the typical system/program startup.
* Installation of malicious scripts or software that automatically starts.
* Creation of additional high-privileged backdoor accounts.

### What to hunt?

* the system's subtle changes and activities
* unrecognized or unexpected scripts running at startup
* spotting unusual scheduled tasks
* noticing irregularities in system registry keys
{% endtab %}

{% tab title="Command and Control" %}
* Command and Control Tactic (TA0011)
* an adversary communicates with the compromised systems within a target network
* attacker usually directs or continuously issues remote commands to the compromised system to fulfil the attacker's objectives
* provide a lifeline between the attacker and the infiltrated network, enabling two-way communication
* attacker solidifies their control over the compromised systems

### Examples

* Standard network protocols, such as DNS, ICMP, HTTP/s.
* Known cloud-based services.
* Encrypted custom HTTP/s server.

### What to hunt?

* [Egress traffic](#user-content-fn-1)[^1]&#x20;
* [Ingress traffic](#user-content-fn-2)[^2]&#x20;
* [Cleartext traffic](#user-content-fn-3)[^3]
* [Encrypted traffic](#user-content-fn-4)[^4]
{% endtab %}

{% tab title="Dicovery" %}
* Discovery Tactic (TA0007)
* actions an attacker may take to understand better the systems and networks they have infiltrated.
* involves identifying system and network configurations, finding sensitive data, or identifying other potential targets within the network.

### Examples

* Obtaining current user information and privileges, such as groups and accessible assets.
* Enumerating host information, such as its operating system, installed applications, and implemented security controls.
* Understanding internal network topology through hosts and services scanning.
* Listing internal domain information, such as domain users, groups, and access control lists.

### What to hunt?

* [unusual information-gathering activities](#user-content-fn-5)[^5]
{% endtab %}

{% tab title="Privilege Escalation" %}
* Privilege Escalation Tactic (TA0004)
* allow an attacker to gain higher privileges or permissions on a system or network
* it can provide the attacker with increased access and control

### Examples

* Exploiting of privilege escalation vulnerabilities.
* Using valid accounts with higher privileges.
* Abusing misconfigured access controls.
* Leveraging host misconfiguration on services and applications.

### What to hunt?

* unusual events executed by privileged accounts
* Abusing of excessive service permissions
{% endtab %}

{% tab title="Credential Access" %}
* Credential Access Tactic (TA0006)
* to steal or discover valid account usernames and passwords (or hashes)
* allowing them to escalate privileges or gain access to other systems or network resources

### Examples

* Dumping credentials in memory or the disk.
* Enumerating files containing credentials (scripts or browser files).
* Dumping domain credentials.
* Credential spraying and brute-forcing.
* Reusing discovered passwords or hashes on other accounts.

### What to hunt?

* indicators of adversaries attempting to acquire or misuse credentials
{% endtab %}

{% tab title="Lateral Movement" %}
* Lateral Movement Tactic (TA0008)
* attacker’s techniques to navigate a network, leveraging the credentials and sessions harvested during previous attack phases
* enable an attacker to explore a network, find valuable assets, and gain access to them

### Examples

* Exploiting internal remote services and applications.
* Using legitimate administrative tools to access remote hosts.
* Authenticating to other workstations or servers using valid credentials.
* Accessing sensitive information stored in file servers or database servers.

### What to hunt?

* uncovering suspicious authentication events and remote machine access from a haystack of benign login attempts by regular users
*
{% endtab %}
{% endtabs %}



[^1]: suspicious file uploads or connections to a C2 server.

[^2]: intrusion attempts from external sources.

[^3]: may indicate an established connection to a C2 server.

[^4]: high count of connections or bandwidth may indicate unusual activity.

[^5]: * Host reconnaissance activity
    * Internal network scanning
    * Active directory execution
