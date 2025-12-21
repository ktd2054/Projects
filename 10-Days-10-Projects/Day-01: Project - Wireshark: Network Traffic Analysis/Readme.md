# 🕵️ Project 1: Wireshark – Network Traffic Analysis

## 📌 Project Overview

This project demonstrates **real-world network traffic analysis** using **Wireshark**, a core skill for **SOC Level 1 / Junior SOC Analyst roles**.  
The investigation is performed **safely using PCAP files only**, simulating how analysts examine malicious traffic in a real Security Operations Center (SOC).

The objective is to **analyze suspicious network activity**, identify **Indicators of Compromise (IOCs)**, and document findings in a **SOC-style investigation report** ; without executing any malware.

---

## 🎯 Goals 

By completing this project, I demonstrate the ability to:

- ✔ Analyze **real malicious network traffic**
- ✔ Identify **Indicators of Compromise (IOCs)** such as:
  - Malicious IP addresses
  - Suspicious domains
  - Abnormal protocols and ports
- ✔ Explain **why the traffic is malicious**, not just flag it
- ✔ Think and investigate like a **SOC analyst**
- ✔ Write a **clear SOC-style incident report**

> ❗ No malware execution is involved, this is **pure network forensics**.

---

## 🛠️ Tools & Environment

- **Wireshark**
- **PCAP files containing malicious traffic**
- **Virtual Machine (VM)**
- **Host-only / NAT network configuration**

---

## 🔍 Analysis Methodology

### 🧠 Investigation Workflow

1. Load PCAP files into **Wireshark**
2. Review traffic using:
   - Protocol Hierarchy
   - Conversations & Endpoints
   - Display Filters (`http`, `dns`, `tcp.stream`, etc.)
3. Identify suspicious behavior such as:
   - Beaconing patterns
   - Unusual DNS queries
   - Suspicious HTTP requests
4. Extract **Indicators of Compromise (IOCs)**:
   - IP addresses
   - Domains
   - Ports
   - File hashes (if visible in traffic)
5. Correlate findings and explain attacker behavior
6. Document results in a **SOC-style investigation report**

---

## 🔐 Safety Rules (IMPORTANT)

This project strictly follows security best practices:

- ✔ **PCAP files only**
- ✔ **No execution of binaries**
- ✔ **Host-only or NAT networking**
- ✔ **Drag & drop disabled** between Host & VM
- ✔ Analysis performed in a **read-only forensic manner**

> 🛡️ This mirrors real SOC investigation procedures.

---

## 📄 Deliverables

- 📊 Wireshark analysis screenshots
- 📋 List of identified IOCs
- 🧾 SOC Investigation Report including:
  - Incident Summary
  - Traffic Analysis
  - Evidence
  - Conclusion & Recommendations

---

## 🚀 Why This Project Matters

This project is designed to be **employer-ready** and showcases my ability to:

**Detect • Analyze • Explain • Report**



---

## 📌 Next Project

- Project 2: Day 2 – Wireshark: Web Attacks (XSS & SQL Injection)

---

## 📫 Author

**Kshitiz Dhungel**  
Aspiring SOC Analyst | Cybersecurity Enthusiast  
