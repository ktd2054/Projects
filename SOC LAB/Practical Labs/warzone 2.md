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

Q5) What is the name of the payload within the cab file? 

Right click the row with our url from brim and go to open details. A sidebar on right will pop-up and we can find filename gap1.cab. It means we need sha1 hash for analysing. 

<img width="1115" height="726" alt="image" src="https://github.com/user-attachments/assets/38924e2b-2936-41f8-859c-6b457b772486" />

Navigate to virustotal.com and paste the hash. Bingo, its dll file. 

<img width="1742" height="913" alt="image" src="https://github.com/user-attachments/assets/6f25eff2-0086-479f-b5a7-45b0586a97fe" />

=> draw.dll

Q6) What is the user-agent associated with this network traffic?

Go back to Brim, and scroll left for user_agent column.

<img width="768" height="576" alt="image" src="https://github.com/user-attachments/assets/707305a5-e130-41f6-aaf6-e5efec94abcc" />

=> Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 10.0; WOW64; Trident/8.0; .NET4.0C; .NET4.0E)

Q7) What other domains do you see in the network traffic that are labelled as malicious by VirusTotal? Enter the domains defanged and in alphabetical order. (format: domain[.]zzz,domain[.]zzz)

Go to virustotal.com and look for other domains.

<img width="924" height="257" alt="image" src="https://github.com/user-attachments/assets/5e5f4de2-b1b3-4c57-9afd-e6e582f03b05" />

=> a-zcorner[.]com, knockoutlights[.]com

Q8) There are IP addresses flagged as Not Suspicious Traffic. What are the IP addresses? Enter your answer in numerical order and defanged. (format: IPADDR,IPADDR)

Go to Brim, search event_type=="alert" | cut src_ip, dest_ip, alert.category | sort for better limited view. 

<img width="743" height="550" alt="image" src="https://github.com/user-attachments/assets/109b0aca-ab42-40a9-9a8b-f1dfc5cecf6a" />

Have a look under alert.category for Not Suspicious Traffic, we will find two uniq ip addresses. Go to CyberChef,

<img width="1188" height="605" alt="image" src="https://github.com/user-attachments/assets/d0b9018a-944f-4278-9610-7658effd79e3" />

=> 64[.]225[.]65[.]166, 142[.]93[.]211[.]176

Q9) For the first IP address flagged as Not Suspicious Traffic. According to VirusTotal, there are several domains associated with this one IP address that was flagged as malicious. What were the domains you spotted in the network traffic associated with this IP address? Enter your answer in a defanged format. Enter your answer in alphabetical order, in a defanged format. (format: domain[.]zzz,domain[.]zzz,etc)

Get the first IP and paste it in virustotal.com, under realtions tab there are three domains with highest number of detections. 
Defang the IPs, 

=> toptocsicambar[.]xyz, safebanktest[.]top,ulcertification[.]xyz

Q10) Now for the second IP marked as Not Suspicious Traffic. What was the domain you spotted in the network traffic associated with this IP address? Enter your answer in a defanged format. (format: domain[.]zzz)

When I went to virustotal.com, I found 3 domains but all of them were wrong when I submitted. Then i went back to Brim and paste the IP in search bar and investigated until I found one domain, and defanged it.

<img width="788" height="390" alt="image" src="https://github.com/user-attachments/assets/1ac89613-e73d-4eca-a167-58506da1bdfb" />

=> 2partscow[.]top

<img width="787" height="391" alt="image" src="https://github.com/user-attachments/assets/cf06609b-09cc-4a0b-a87d-1bfac2e79626" />

