
# MITRE Frameworks – Complete Notes for SOC Analysts
This document provides detailed notes on key MITRE frameworks aligned with the SOC Level 1
learning path.--
# **Task 1: Introduction**
MITRE develops industry-standard cybersecurity frameworks that help defenders analyze, detect,
mitigate, and understand adversarial behaviors.
These frameworks support SOC workflows: threat hunting, incident response, detection engineering,
and reporting.
Key MITRE Frameworks covered:- **ATT&CK;**- **CAR (Cyber Analytics Repository)**- **D3FEND**- **Other MITRE security projects**--
# **Task 2: MITRE ATT&CK;® Framework**
## **What is ATT&CK;?**
A globally recognized knowledge base of adversary tactics, techniques, and procedures (TTPs).
It maps out real-world attacker behavior in a structured and standardized format.
### **ATT&CK; Structure**
1. **Tactics** – *Why* attackers perform actions (goals).
2. **Techniques** – *How* attackers achieve these goals.
3. **Sub-techniques** – More detailed steps.
4. **Mitigations** – Defensive advice.
5. **Detections** – How SOCs identify activity.
### **ATT&CK; Matrices**- **Enterprise** (Windows, Linux, macOS)- **Mobile**- **ICS** (Industrial Control Systems)
### **Example Technique**- **T1059 – Command and Scripting Interpreter**- Common malicious PowerShell activity- Detection: Command-line logging, script block logging- Mitigation: Restrict PowerShell versions, application allow-listing--
# **Task 3: ATT&CK; in Operation**
ATT&CK; is a practical tool for threat hunting, detection engineering, and incident response.
## **1. Threat Hunting**
Analysts choose tactics (e.g., Execution or Persistence) → hunt relevant techniques → validate with
logs.
## **2. Detection Engineering**
For each technique:- Identify required log sources (Sysmon, EDR, Firewall)- Build detection rules (SIEM/Splunk/Sigma)- Map alerts to ATT&CK; IDs
## **3. Incident Response**
During investigations:- Map observed behavior to ATT&CK; techniques- Understand attacker capabilities- Predict possible next steps
## **4. Reporting**
SOC reports often include:
> “Activity observed correlates to MITRE ATT&CK; techniques T1566 (Phishing) and T1059
(PowerShell).”--
# **Task 4: ATT&CK; for Threat Intelligence**
ATT&CK; helps threat intel teams:- Profile adversary groups- Identify behaviors used by specific campaigns- Track changes in attacker techniques across time
## **Threat Group Mapping**
Groups are listed in ATT&CK; by ID (e.g., **APT29**, **FIN7**).
Each group has:- Known tools- Techniques used- Campaign history
## **Benefits for SOC**- Helps predict attacker behavior- Supports proactive blocking of known techniques- Enables enriching alerts with threat context--
# **Task 5: Cyber Analytics Repository (CAR)**
## **What is CAR?**
CAR is a repository of behavioral analytics designed for defenders.
It translates ATT&CK; techniques into:- Detectable events- Log source requirements- Example Splunk/ELK queries
## **Example CAR Analytics**- **CAR-2019-04-002:** Detect PowerShell download cradle
Detection: Look for commands like
`powershell -nop -w hidden -command "IEX (New-Object Net.WebClient).DownloadString(...)"`- **CAR-2020-04-003:** Detect unusual lateral movement via SMB
Required logs: Sysmon, Windows Event Logs, EDR
### Why CAR matters:- Directly helps SOC analysts create detections- Bridges the gap between ATT&CK; theory and real SIEM implementation--
# **Task 6: MITRE D3FEND Framework**
## **What is D3FEND?**
D3FEND is a defensive counterpart to ATT&CK.;
It maps attacker techniques to defensive countermeasures.
### D3FEND Categories:
1. **Harden →** Strengthening systems
2. **Detect →** Identify malicious events
3. **Isolate →** Restrict attacker movement
4. **Deceive →** Mislead attackers
5. **Evict →** Remove attacker presence
### Example Mapping:- ATT&CK; Technique **T1059 (PowerShell execution)**
→ D3FEND Defensive:- **Execution Isolation**- **Behavioral Monitoring**- **Process Whitelisting**
### Why D3FEND is important:- Helps SOC teams choose proper mitigations- Useful for blue team architecture planning--
# **Task 7: Other MITRE Projects**
MITRE develops additional community tools for broader security use:
### **1. CALDERA**
Automated adversary emulation platform
Used for:- Blue team exercises- Testing SOC detections- Red team operations
### **2. Shield Framework**
Focused on active defense:- Honeypots- Deception technology- Engagement techniques
### **3. CHARADE**
Research project analyzing deception techniques.
### **4. MITRE CWE (Common Weakness Enumeration)**
A catalog of software weakness types.
### **5. MITRE CAPEC (Common Attack Pattern Enumeration & Classification)**
Database describing common attack patterns.--
# **Task 8: Conclusion**
MITRE frameworks give SOC analysts:- A structured understanding of attacker behavior- A guided approach to detection, response, and threat hunting- Defensive strategies to counter tools, malware, and TTPs- A shared language for reporting and communication
