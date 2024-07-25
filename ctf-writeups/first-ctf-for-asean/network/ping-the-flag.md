# Ping The Flag

<figure><img src="../../../.gitbook/assets/image (108).png" alt=""><figcaption></figcaption></figure>

***

## Solution

Open the capture.pcap in wireshark.

Notice that the all the captured networks are **ICMP** packets.&#x20;

<figure><img src="../../../.gitbook/assets/image (109).png" alt=""><figcaption></figcaption></figure>

The main focus here is the destination address which is **155.138.162.112**

By looking at each of the packets, we can see that some data being sent to that IP address.&#x20;

<figure><img src="../../../.gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

Notice that the data in each of the packets are different. It is a sign of data exfiltration using ICMP.

Filter out the data from each of the packets and combine them all together. Then convert them to ASCII characters. Both **scapy** and **tshark** can be use to solve this challenge.



{% code title="solve.py" lineNumbers="true" %}
```python
from scapy.all import *

data = "capture.pcap"
a = rdpcap(data)
sessions = a.sessions()
result = ""

for session in sessions:
    for packet in sessions[session]:
        if IP in packet and packet[IP].dst == '155.138.162.112' and ICMP in packet:
            try:
                payload = packet[ICMP].load.decode('ascii')
                if payload.strip():
                    result += payload + " "
            except UnicodeDecodeError:
                result += "[Non-ASCII Data] "

if result:
    print(result)
else:
    print("No ASCII payloads found for the specified conditions.")
```
{% endcode %}

By running the script, we successfully retrieve the data in the ICMP packets in morse code.

<figure><img src="../../../.gitbook/assets/image (111).png" alt=""><figcaption></figcaption></figure>

Decode the morse code, we can see some rubbish letter 'S' surrounding our flag

<figure><img src="../../../.gitbook/assets/image (112).png" alt=""><figcaption></figcaption></figure>

Below is the decoded text after cleaning up.

`THEFLAGIS82C6E7A048BC79DCA49C0A0462CEFFC4`

***

## Flag

82C6E7A048BC79DCA49C0A0462CEFFC4
