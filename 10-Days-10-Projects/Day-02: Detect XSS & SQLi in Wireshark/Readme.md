# Day 2 - 🔍 Web Attack Detection (XSS & SQL Injection) using Wireshark

## 📌 Project Overview
This project demonstrates my ability to **detect and analyze real-world web attacks** such as **SQL Injection (SQLi)** and **Cross-Site Scripting (XSS)** at the **network traffic level** using **Wireshark**.

The goal is to show how a **SOC Analyst** can:
- Identify malicious web requests
- Extract Indicators of Compromise (IOCs)
- Explain *why* traffic is malicious
- Document findings in a SOC-style investigation report

All attacks were conducted **safely in a controlled lab environment** against a deliberately vulnerable application.

---

## 🎯 Skills Demonstrated 
- Network traffic analysis using Wireshark
- Detection of SQL Injection and XSS payloads
- Understanding HTTP request/response behavior
- Identifying malicious patterns in URLs and parameters
- SOC-style documentation and reporting
- Safe testing methodology (no live targets, no malware execution)

---

## 🧪 Lab Environment

| Component | Details |
|---------|--------|
| Attacker | Kali Linux |
| Target | DVWA (Damn Vulnerable Web Application) – Docker |
| Network | NAT / Host-only |
| Protocol | HTTP |
| Capture Tool | Wireshark |

> ⚠️ **Safety Note:**  
> All testing was performed against a **local vulnerable web application** running inside a VM.  
> No external systems or real users were targeted.

---

## 🛠 Tools Used
- **Wireshark** – Network packet capture and analysis
- **DVWA (Docker)** – Vulnerable web application
- **Kali Linux** – Attacker machine
- **Browser** – Generating web traffic


