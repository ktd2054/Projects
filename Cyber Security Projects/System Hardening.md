
<img width="737" height="206" alt="image" src="https://github.com/user-attachments/assets/177e5214-fcd4-464f-bcb5-b9579ce34a6e" />

---

# 🏰 Part 2 – Active Directory Auditing with PingCastle

PingCastle identifies:

- Weak authentication
- Legacy protocols
- Stale objects
- Privilege issues

<img width="1700" height="544" alt="image" src="https://github.com/user-attachments/assets/f9a624dc-0c0e-42b9-8c36-f34af77e99f9" />

Run health check.

<img width="954" height="606" alt="image" src="https://github.com/user-attachments/assets/5593052a-c7bd-4d3b-9cfc-d7f3a46fc98f" />

Open report.

<img width="1342" height="783" alt="image" src="https://github.com/user-attachments/assets/39f7f621-8601-473e-b42a-fbc7dfabcd55" />

Domain risk: **50/100**

<img width="982" height="566" alt="image" src="https://github.com/user-attachments/assets/315521d5-b318-42b7-8d0c-5f7953dfb26d" />

Findings include potential account takeover and sniffing.

<img width="1255" height="243" alt="image" src="https://github.com/user-attachments/assets/fc29e77b-e8cd-4f6e-be84-f7725c8a324b" />

Reviewing stale objects:

<img width="1352" height="694" alt="image" src="https://github.com/user-attachments/assets/26aacd9e-dbe9-41a6-bfdd-9c3cc311043e" />

---

## NTLM Explanation

**NTLM (NT LAN Manager)** is an old Windows authentication protocol.

Problems:

- Vulnerable to relay attacks  
- Weak cryptography  
- Enables credential harvesting  

Modern environments should use **Kerberos**, which provides:

- Mutual authentication  
- Encrypted tickets  
- Replay protection  

Disabling NTLM significantly reduces lateral movement risk.

---

## Remediating NTLM

Create GPO: `Disable NTLM`

<img width="1082" height="482" alt="image" src="https://github.com/user-attachments/assets/dd03102a-3d8e-40c3-8ad6-21d7f03390b2" />

<img width="1224" height="693" alt="image" src="https://github.com/user-attachments/assets/47f4f21f-768e-47f3-939e-f7ef0bed73d9" />

Navigate:

Policies → Security Settings → Local Policies → Security Options

<img width="576" height="88" alt="image" src="https://github.com/user-attachments/assets/1a455ba6-1a47-43ca-9353-85a85f841319" />

Configure LAN Manager authentication.

<img width="446" height="322" alt="image" src="https://github.com/user-attachments/assets/d58de24c-cc25-4fb9-acc5-843257ef9671" />

Push policy.

<img width="433" height="200" alt="image" src="https://github.com/user-attachments/assets/5c73c336-760b-4ad8-81b8-2b63164d351d" />

<img width="1531" height="318" alt="image" src="https://github.com/user-attachments/assets/4de4f410-3863-446d-a083-e0dfb38e2bd8" />

Re-run PingCastle.

<img width="1463" height="479" alt="image" src="https://github.com/user-attachments/assets/f05f1dd2-c210-47b4-a6cd-0eaa37b11d17" />

NTLM-related risks reduced.

---

# 🐧 Part 3 – Linux Hardening with Lynis

**OS:** Kali Linux  
**Tool:** Lynis  

---

## System Update

<img width="856" height="164" alt="image" src="https://github.com/user-attachments/assets/95fc85f0-b201-4e0f-a0f5-5ce2361e7349" />

Encountered dpkg error.

Fix followed from:

https://askubuntu.com/questions/591855/how-can-i-fix-e-sub-process-usr-bin-dpkg-returned-an-error-code-2

Reconfigured dpkg:

<img width="1007" height="722" alt="image" src="https://github.com/user-attachments/assets/9041be88-7593-46a9-ad12-475fa2ea66ce" />

Issue resolved.

---

## Installing Lynis

<img width="486" height="183" alt="image" src="https://github.com/user-attachments/assets/009f2509-7987-480f-861d-da0ff19641cd" />

---

## Running Lynis Audit

<img width="795" height="359" alt="image" src="https://github.com/user-attachments/assets/394bce84-c4ae-413c-9d0e-ec6bbdad61a6" />

Lynis provides:

- Security warnings  
- Hardening suggestions  
- Kernel checks  
- File permission issues  
- Service exposure  

These recommendations guide further Linux hardening.

---

# ✅ Conclusion

This lab demonstrates:

- Windows baseline auditing  
- GPO-based hardening  
- Active Directory risk assessment  
- NTLM removal  
- Linux security auditing  

These are foundational skills for:

- IT Support  
- Infrastructure Administration  
- SOC Level 1  
- Blue Team operations  

This project reflects real-world enterprise security workflows.

---
