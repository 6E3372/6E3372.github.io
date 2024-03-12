# Foothold

There are a bunch of tactics we can found in [MITRE ATT\&CK Frameworks](https://attack.mitre.org/). The following are some of the examples.



{% tabs %}
{% tab title="Initial Access" %}
* Initial Access Tactic (TA0001)
* techniques and strategies to breach an organisation
* focus on delivering payload to target system or network

### Objective

* to gain a foothold in the network

### How?

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

### How?

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

### How?

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

### How?

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

### How?

* Standard network protocols, such as DNS, ICMP, HTTP/s.
* Known cloud-based services.
* Encrypted custom HTTP/s server.

### What to hunt?

* [Egress traffic](#user-content-fn-1)[^1]&#x20;
* [Ingress traffic](#user-content-fn-2)[^2]&#x20;
* [Cleartext traffic](#user-content-fn-3)[^3]
* [Encrypted traffic](#user-content-fn-4)[^4]
{% endtab %}
{% endtabs %}



[^1]: suspicious file uploads or connections to a C2 server.

[^2]: intrusion attempts from external sources.

[^3]: may indicate an established connection to a C2 server.

[^4]: high count of connections or bandwidth may indicate unusual activity.
