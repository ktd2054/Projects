
# Cyber Kill Chain – Detailed Notes for SOC Analysts
The **Cyber Kill Chain**, developed by Lockheed Martin, is a framework that breaks down the stages
of a cyber attack.
Understanding this helps SOC analysts detect and disrupt attacks early, ideally before they progress
into execution or data loss.--
## **1. Reconnaissance**
### Description:
The attacker collects information about the target: employees, infrastructure, emails, exposed services,
technologies.
### What attackers do:- Gather emails for phishing.- Scan network ranges for open ports (e.g., Nmap).- Passive intelligence from OSINT platforms (Shodan, LinkedIn, GitHub leaks).
### SOC Detection:- Unusual scanning activity.- Suspicious botnet queries to public services.- Threat intel showing interest in your org.--
## **2. Weaponization**
### Description:
The attacker creates the payload—usually combining an exploit with malware.
### Examples:- Creating a malicious macro document (Word + VBA payload).- Crafting a PDF exploit with embedded shellcode.- Building a malware loader or trojan.
### SOC Detection:
This stage happens *off-network*, so defenders detect it indirectly via:
- Malware signatures- Sandbox analysis- Threat intelligence feeds--
## **3. Delivery**
### Description:
The attacker sends the weaponized payload to the target.
### Delivery Methods:- Phishing emails with malicious attachments- Malicious links (HTML smuggling, credential harvesters)- Watering hole websites- USB drops
### SOC Detection:- Email filtering alerts (malicious attachment)- URL reputation block events- User-reported phishing attempts- Proxy logs showing requests to suspicious domains--
## **4. Exploitation**
### Description:
The malicious payload is executed on the victim machine.
### Examples:- User opens malicious doc → macro runs- Browser exploit triggers vulnerable plugin- RCE vulnerability exploited on a public-facing server
### SOC Detection:- EDR detects exploit shellcode behavior
- Application crashes/anomalies- Suspicious PowerShell or cmd activity--
## **5. Installation**
### Description:
Attacker installs persistence mechanisms or establishes a backdoor.
### Examples:- Dropping a remote access trojan (RAT)- Writing registry autorun keys- Creating scheduled tasks- DLL sideloading
### SOC Detection:- New services/processes created- Registry autorun changes- File creation in unusual directories (`C:\ProgramData`, `%AppData%`)- EDR detects persistence indicators--
## **6. Command and Control (C2)**
### Description:
Compromised host communicates with attacker servers.
### Examples:- HTTPS encrypted beaconing- DNS tunneling- Custom C2 frameworks (Cobalt Strike, Sliver)
### SOC Detection:- Network anomaly detection- Unusual JA3 TLS fingerprints
- Repeated beacon intervals- Outbound traffic to rare/dangerous countries--
## **7. Actions on Objectives**
### Description:
Attacker achieves their goals—espionage, data exfiltration, ransomware deployment, lateral
movement.
### Possible Objectives:- Credential theft (LSASS dump, Mimikatz)- Lateral movement (SMB, PsExec, RDP)- Exfiltration (FTP, cloud drives, DNS-exfil)- Encryption of files (ransomware)
### SOC Detection:- Mass file access anomalies- Large outbound data transfers- Privilege escalation attempts- Ransom notes or encryption behavior--
## **Why SOC Analysts Use the Cyber Kill Chain**- Identifies where attacks can be stopped early- Helps map detections to stages- Guides incident response strategies- Useful for MITRE ATT&CK; correlation--
## **Summary Table**
| Stage | Key Attacker Activity | SOC Detection Focus |
|-------|------------------------|----------------------|
| Recon | Info gathering | OSINT monitoring, scanning detection |
| Weaponization | Build payload | Threat intel |
| Delivery | Send payload | Email/proxy logs |
| Exploitation | Execute exploit | EDR alerts |
| Installation | Persistence | Registry, autoruns, new services |
| C2 | Beaconing | Network monitoring |
| AOO | Final attack | Lateral movement, exfil, ransomware 
