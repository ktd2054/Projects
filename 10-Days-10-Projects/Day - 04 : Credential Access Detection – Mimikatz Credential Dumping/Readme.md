# 🔐 SOC Credential Access Investigation – Mimikatz

## 🎯 Project Overview
This project demonstrates a **SOC Level 1 investigation** of a **credential dumping attack** using **real Windows EVTX logs**. 
The case focuses on detecting **Mimikatz-style LSASS access** through Sysmon events and validating the activity using SIEM analysis.

---

## 🧰 Tools & Technologies
- Windows Event Logs (EVTX)
- Sysmon
- Splunk (SIEM)
- MITRE ATT&CK Framework

---

## 🔍 What Was Investigated
- Suspicious process execution
- Unauthorized access to `lsass.exe`
- Indicators of credential dumping
- Attack timeline reconstruction

---

## 🚨 Key Findings
- A malicious process accessed LSASS memory
- Activity matched known **credential dumping behavior**
- High risk of credential compromise detected

---

## 🗺️ MITRE ATT&CK Mapping
- **Credential Access** – OS Credential Dumping (T1003)
- **Execution** – Command Execution (T1059)

---

## 📄 Deliverables
- Investigation notes & timeline
- Extracted Indicators of Compromise (IOCs)
- SOC-style incident report
- MITRE ATT&CK mapping

---

## 🧑‍💼 Skills Demonstrated
- SIEM alert triage
- Windows log analysis
- Threat detection & validation
- Incident reporting
- Blue Team fundamentals

---

