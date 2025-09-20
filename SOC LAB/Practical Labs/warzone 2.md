# TryHackMe: Warzone 2 Write-up

Welcome to the sequel of warzone. The same tools will be used. 

<img width="799" height="209" alt="image" src="https://github.com/user-attachments/assets/9afaf4a6-a347-47cc-a3eb-1edf2643294d" />

# Task 1: Another day, another alert.

You work as a Tier 1 Security Analyst L1 for a Managed Security Service Provider (MSSP). Again, you're tasked with monitoring network alerts.

An alert triggered: Misc activity, A Network Trojan Was Detected, and Potential Corporate Privacy Violation. 

The case was assigned to you. Inspect the PCAP and retrieve the artifacts to confirm this alert is a true positive. 

Your tools:

- Brim
- Network Miner
- Wireshark

Deploy the machine attached to this task; it will be visible in the split-screen view once it is ready.

If you don't see a virtual machine load then click the Show Split View button.

### Answer the questions below

Q1) What was the alert signature for A Network Trojan was Detected?

Open Zone2.pcap file with Brim app and search event_type=="alert", scroll left for details under alert.signature column.

=> ET MALWARE Likely Evil EXE download from MSXMLHTTP non-exe extension M2

<img width="1111" height="583" alt="image" src="https://github.com/user-attachments/assets/ae32db33-c3b0-4e97-a048-27df3d4a8e09" />


Q2) What was the alert signature for Potential Corporate Privacy Violation?

Look under alert.signature and alert.category column for answer. 

=> ET POLICY PE EXE or DLL Windows file download HTTP

Q3) What was the IP to trigger either alert? Enter your answer in a defanged format. 

Look for destination ip column for either alerts. Here, IP is same for both both category. Use query: event_type=="alert" | cut src_ip, alert.signature, alert.category | sort for limited search. 

<img width="1039" height="589" alt="image" src="https://github.com/user-attachments/assets/795c99d1-3421-4434-ab6a-b71050b40fc1" />

Go to CyberChef to Defang the IP address. 

=>  185[.]118[.]164[.]8

Q4) Provide the full URI for the malicious downloaded file. In your answer, defang the URI

Search _path=="http" and look for our ip from Q3. Let's find host and url under host and uri column. 

<img width="934" height="489" alt="image" src="https://github.com/user-attachments/assets/86cf6567-49b2-4ada-bc6d-9fe833d9abbf" />

Copy the host and uri name and paste it to cyberchef.com to get defanged url.

<img width="1532" height="626" alt="image" src="https://github.com/user-attachments/assets/da3ae41d-9434-4f91-9f04-d354cbab9392" />

=> awh93dhkylps5ulnq-be[.]com/czwih/fxla[.]php?l=gap1[.]cab

Q5) 

Right click the row with our url from brim and go to open details. A sidebar on right will pop-up and we can find filename gap1.cab. It means we need sha1 hash for analysing. 

<img width="1115" height="726" alt="image" src="https://github.com/user-attachments/assets/38924e2b-2936-41f8-859c-6b457b772486" />

Navigate to virustotal.com and paste the hash. Bingo, its dll file. 

<img width="1742" height="913" alt="image" src="https://github.com/user-attachments/assets/6f25eff2-0086-479f-b5a7-45b0586a97fe" />

=> draw.dll
