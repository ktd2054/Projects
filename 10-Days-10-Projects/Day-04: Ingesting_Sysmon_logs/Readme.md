## 🛡️ Ingesting Sysmon Logs into Splunk | SOC Lab

Set up **Sysmon** and **Splunk Enterprise** on Windows and Kali VMs to practice real SOC-style log ingestion and validation.

### 🔍 What I Did
- Generated test activity (📝 Notepad execution, 🌐 ping, app usage)
- Verified Sysmon events in **Event Viewer → Sysmon → Operational**
- Installed **Splunk Add-on for Microsoft Windows** & **Sysmon Add-on**
- Ingested Sysmon logs into Splunk and validated visibility

### 🧠 Key Learnings
- ❌ Splunk does not reliably parse uploaded `.evtx` files
- ✅ Converting logs to **XML / TXT** enabled successful ingestion
- ⚙️ Correct **source types and add-ons** are critical for log visibility

### 🎯 Outcome
- Sysmon events successfully searchable in Splunk
- Gained hands-on experience with **log ingestion troubleshooting** and **SOC workflows**

### 🛠️ Tools
Sysmon • Splunk Enterprise • Windows Event Viewer • Kali Linux
