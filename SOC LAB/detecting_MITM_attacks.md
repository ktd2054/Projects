# Writeup: TryHackMe - Detecting MITM Attacks

IBM states "A man-in-the-middle (MITM) attack is a cyberattack in which a hacker steals sensitive information by eavesdropping on communications between two online targets such as a user and a web application."
(<link> https://www.ibm.com/think/topics/man-in-the-middle</link>)

Here, an individual or an attacker positions themselves inbetween communication terminals to intercept, modify or redirect the traffic without anybody's knowledge. They eavesdrop to steal sensitive information such as credntils
or credit card information or may inject malicious content. If the authentication or encryption is weak then attckers will easily target any individual or organization. 

### The two steps of MITM attack:

- interception of network traffic by placing themselves into communication stream and exploiting weak protocols or using techniques like ARP, DNS or IP spoofing.
- accessing or modifying communication, decryption of encoded data or injecting harmful content such as fake login forms

### Common Types of MITM attack

- Packet sniffing: Capturing unencrypted data packets exchanged over a network, often on open Wi-Fi.
- Session hijacking: Stealing and using session tokens to impersonate users.
- SSL stripping: Downgrading HTTPS connections to insecure HTTP to steal or alter data transferred.
- DNS spoofing: Redirecting legitimate website traffic to fraudulent domains by manipulating DNS responses.
- IP spoofing: Crafting malicious IP packets that appear to come from trusted systems.
- Rogue Wi-Fi access point: Creating fake networks to intercept user traffic.

## MITM and Cyber Kill Chain

A widely adopted model for detecting MITM attack is the Cyber Kill Chain, a framework that sequences the typical stages of an advanced cyber intrusion.
The Cyber Kill Chain will help us to understand and protect against ransomware attacks, security breaches as well as Advanced Persistent Threats (APTs

The framework consists of seven distinct phases:

- Reconnaissance: The adversary gathers intelligence on the target to identify vulnerabilities.
- Weaponization: The adversary couples an exploit with a malicious payload into a deliverable package.
- Delivery: The adversary transmits the weaponized package to the targeted environment.
- Exploitation: The adversary's code is triggered, and it takes advantage of a software, hardware, or human vulnerability to gain initial access.
- Installation: The adversary installs malware or establishes a persistent backdoor on the compromised asset.
- Command & Control (C2): The adversary establishes a covert channel to communicate with and control the compromised asset.
- Actions on Objectives: The adversary executes their ultimate goals, such as data exfiltration, destruction, or lateral movement.

There are two phases where an advesary performs usch attacks:

- As an Exploitation Technique, MITM attack gains trust and designs the limitaions of network protocols like ARP and DNS. After manipulating these protocols attackers intercepts the communication channel
  known as exploitation,as it violates the integrity of the network which is more benifical for an attacker to eavesdrop.

- As anInstallation Vector, when the attcker establishes the position, initial step is to control the data stream and uses it as delivery mechanism for malicious payload to deploy
 malicious tools onto the victims system.


## ARP Spoofing

Before ARP Spoofing, 

- What is ARP Protocol?

ARP (Address Resolution Protocol) maps IP addresses to MAC addresses in a local network. When a device wants to send data to another IP, it first asks: "Who has this IP?” The correct device replies
with its MAC address.

Now back to topic,

In ARP spoofing, an attacker sends fake ARP replies to trick devices into associating the attacker’s MAC address with a legitimate IP, usually the default gateway. 
This allows the attacker to intercept, modify, or redirect traffic.

### Indicators of ARP Spoofing 

- Duplicate MAC-to-IP Mappings: Multiple MAC addresses claiming the same IP address. Indicates impersonation.
- Unsolicited ARP Replies: High number of ARP replies without matching requests ("gratuitous ARP").
- Abnormal ARP Traffic Volume: A Large number of ARP packets in short intervals.
- Unusual Traffic Routing: Traffic rerouted through the attacker’s MAC.
- Gateway Redirection Patterns: Multiple destination MACs for the same gateway IP.
- ARP Probe / Reply Loops: Many ARP requests with Who has 192.168.1.x? Tell 192.168.1.y patterns.


## Lab Exercise

Opening ready to investigate network-traffic.pcap file in wireshark using THM VMs.

In the filter: <i> arp </i> - the following image shows all the request and replies (who-has and is-at) poinitng to both ARP request and response.

<img width="1384" height="501" alt="image" src="https://github.com/user-attachments/assets/37a46f48-1f8e-48ec-9eb9-74196d3a0ebe" />






















