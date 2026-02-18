# 🛡️ System Hardening & Security Auditing Lab  
Environment: Windows Server 2022 Domain + Kali Linux  
Tools: Microsoft Compliance Toolkit, Group Policy Management, PingCastle, Lynis  

---

## 📌 Project Overview

This project demonstrates practical system hardening and security auditing across both **Windows Active Directory** and **Linux systems**.

The objective is to:

- Assess default security posture  
- Compare configurations against Microsoft security baselines  
- Apply hardened Group Policy Objects (GPOs)  
- Identify Active Directory weaknesses  
- Reduce legacy authentication risks (NTLM)  
- Audit Linux using Lynis  
- Validate improvements after remediation  

This simulates real-world **Level 1/2 IT Support + SOC foundational tasks**, including:

- Policy auditing  
- Identity security  
- Authentication hardening  
- Endpoint configuration  
- Vulnerability assessment  

---

## 🎯 Why This Project Is Important

Many organizations operate with:

- Weak audit policies  
- Legacy authentication protocols  
- Stale Active Directory objects  
- Limited logging  
- Poor baseline enforcement  

These gaps allow:

- Credential theft  
- Lateral movement  
- Network sniffing  
- Account takeover  

This lab focuses on identifying and reducing these risks.

---

# 🪟 Part 1 – Auditing Windows Using Microsoft Security Baselines

## Downloading Microsoft Compliance Toolkit

Search **Microsoft Compliance Toolkit** and download the version matching your OS (Windows Server 2022).

<img width="1007" height="257" alt="image" src="https://github.com/user-attachments/assets/633feb51-2338-4aca-a2c5-3f196505cc12" />

These tools allow administrators to:

- Import Microsoft-recommended GPO baselines  
- Compare current system policies  
- Identify misconfigurations  
- Apply hardened security settings  

---

## Running Policy Analyzer Toolkit

<img width="909" height="318" alt="image" src="https://github.com/user-attachments/assets/672cfdac-6ca3-41ef-b0f9-330e3707e6ac" />

Run Policy Analyzer **as Administrator**.

<img width="609" height="520" alt="image" src="https://github.com/user-attachments/assets/5878dbbf-dc8f-4986-b915-e02d9347fd6c" />

Click **Add → Add files from GPOs**

<img width="728" height="358" alt="image" src="https://github.com/user-attachments/assets/fc36f9f3-fea4-44eb-9827-ccdfb343afd6" />

Import the GPO folder.

<img width="931" height="471" alt="image" src="https://github.com/user-attachments/assets/6969f9e8-adcd-4bb1-a0ed-fa9b9d4e46bc" />

Name the imported baseline.

<img width="500" height="270" alt="image" src="https://github.com/user-attachments/assets/7ff511fa-d29a-49ea-b8c3-c1e9ad276da5" />

---

## Comparing Baseline vs Current System

Click **Compare to Effective State**

<img width="975" height="436" alt="image" src="https://github.com/user-attachments/assets/8412f152-9b09-4cdd-a7c5-0b944e6000b7" />

Yellow indicates differences between recommended and current settings.

<img width="1183" height="352" alt="image" src="https://github.com/user-attachments/assets/942a7e4c-f37e-4fcf-b316-d1a1803fe1f9" />

---

## Selecting Policies

<img width="865" height="18" alt="image" src="https://github.com/user-attachments/assets/d78c0c08-afd8-48fd-a960-d5d98e664d5d" />

Editing Other Account Management Events

<img width="661" height="168" alt="image" src="https://github.com/user-attachments/assets/078cdf51-8344-4841-9c5b-a357c6be4610" />

After gpupdate:

<img width="891" height="34" alt="image" src="https://github.com/user-attachments/assets/ce2f8b34-2cd1-424e-b943-3c20a0544c00" />

---

# 🧩 Applying GPO Hardening

Open Group Policy Management.

<img width="455" height="125" alt="image" src="https://github.com/user-attachments/assets/08e7866b-3caa-4d28-87e1-155efe4a48db" />

Create GPO: Logging Server and Workstation Policies

Navigate:

Windows Settings → Security Settings → Advanced Audit Policy Configuration

<img width="959" height="98" alt="image" src="https://github.com/user-attachments/assets/71b4b881-04d5-4e69-b239-bef7bc439edb" />

Credential Validation conflict:

<img width="311" height="138" alt="image" src="https://github.com/user-attachments/assets/1c4672c8-91b6-437c-a4c7-e8f9cb457bc4" />

<img width="1229" height="623" alt="image" src="https://github.com/user-attachments/assets/2797cb2d-5428-4b81-8e26-12e722f4edf2" />

Enable Success and Failure.

Kerberos auditing:

<img width="793" height="345" alt="image" src="https://github.com/user-attachments/assets/a7cef346-5621-4258-babe-147b91fc5bda" />

Apply:

gpupdate /force  
gpresult /r /scope computer  

<img width="737" height="206" alt="image" src="https://github.com/user-attachments/assets/177e5214-fcd4-464f-bcb5-b9579ce34a6e" />

---

# 🏰 Active Directory Auditing with PingCastle

<img width="1700" height="544" alt="image" src="https://github.com/user-attachments/assets/f9a624dc-0c0e-42b9-8c36-f34af77e99f9" />

Run health check.

<img width="954" height="606" alt="image" src="https://github.com/user-attachments/assets/5593052a-c7bd-4d3b-9cfc-d7f3a46fc98f" />

Open report.

<img width="1342" height="783" alt="image" src="https://github.com/user-attachments/assets/39f7f621-8601-473e-b42a-fbc7dfabcd55" />

Risk score 50/100.

<img width="982" height="566" alt="image" src="https://github.com/user-attachments/assets/315521d5-b318-42b7-8d0c-5f7953dfb26d" />

Stale objects:

<img width="1255" height="243" alt="image" src="https://github.com/user-attachments/assets/fc29e77b-e8cd-4f6e-be84-f7725c8a324b" />

<img width="1352" height="694" alt="image" src="https://github.com/user-attachments/assets/26aacd9e-dbe9-41a6-bfdd-9c3cc311043e" />

---

## NTLM Explanation

NTLM is a legacy Windows authentication protocol vulnerable to relay and credential theft.

Kerberos is preferred because it provides:

- Mutual authentication  
- Encrypted tickets  
- Replay protection  

---

## Disable NTLM

Create GPO: Disable NTLM

<img width="1082" height="482" alt="image" src="https://github.com/user-attachments/assets/dd03102a-3d8e-40c3-8ad6-21d7f03390b2" />

<img width="1224" height="693" alt="image" src="https://github.com/user-attachments/assets/47f4f21f-768e-47f3-939e-f7ef0bed73d9" />

Navigate to Security Options.

<img width="576" height="88" alt="image" src="https://github.com/user-attachments/assets/1a455ba6-1a47-43ca-9353-85a85f841319" />

Configure LAN Manager:

<img width="446" height="322" alt="image" src="https://github.com/user-attachments/assets/d58de24c-cc25-4fb9-acc5-843257ef9671" />

Push policy.

<img width="433" height="200" alt="image" src="https://github.com/user-attachments/assets/5c73c336-760b-4ad8-81b8-2b63164d351d" />

<img width="1531" height="318" alt="image" src="https://github.com/user-attachments/assets/4de4f410-3863-446d-a083-e0dfb38e2bd8" />

Re-run PingCastle:

<img width="1463" height="479" alt="image" src="https://github.com/user-attachments/assets/f05f1dd2-c210-47b4-a6cd-0eaa37b11d17" />

---

# 🐧 Linux Hardening – Kali + Lynis

Update system:

<img width="856" height="164" alt="image" src="https://github.com/user-attachments/assets/95fc85f0-b201-4e0f-a0f5-5ce2361e7349" />

Fix dpkg error using:

https://askubuntu.com/questions/591855/how-can-i-fix-e-sub-process-usr-bin-dpkg-returned-an-error-code-2

<img width="1007" height="722" alt="image" src="https://github.com/user-attachments/assets/9041be88-7593-46a9-ad12-475fa2ea66ce" />

---

## Install Lynis

<img width="486" height="183" alt="image" src="https://github.com/user-attachments/assets/009f2509-7987-480f-861d-da0ff19641cd" />

---

## Run Lynis

<img width="795" height="359" alt="image" src="https://github.com/user-attachments/assets/394bce84-c4ae-413c-9d0e-ec6bbdad61a6" />

Lynis provides system hardening recommendations including kernel, services, permissions, and logging.

---

# ✅ Conclusion

This lab demonstrates:

- Windows security baseline auditing  
- Group Policy hardening  
- Active Directory risk analysis  
- NTLM removal  
- Linux auditing with Lynis  

These skills are foundational for:

- IT Support  
- Infrastructure Administration  
- SOC Level 1  
- Blue Team operations  

This project reflects real enterprise security workflows.

---
