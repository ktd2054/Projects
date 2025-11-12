# Perimeter Logs: Investigating a Breach

This section falls under Network Security Essentials from TryHackMe. This is a challenge hands-on lab given to learners. 

### Incident Scenario

Initech Corp, a mid-sized financial services company, has recently deployed a new firewall and intrusion detection system (IDS) to monitor its network perimeter. Over the past month, security analysts have noticed abnormal traffic patterns, but the SOC team has been overwhelmed and missed deeper analysis.

As a new security analyst, you have been tasked with reviewing one month of perimeter logs to determine what techniques the adversary used, and whether they succeeded in breaching the perimeter.

You have been given three sets of logs from the time of the incident. The logs can be found in the Perimeter_logs/challenge directory on the Desktop.

- Firewall Logs:firewall.log

- WAF Logs:ids_alerts.log 

- VPN Logs:vpn_auth.log 

<img width="656" height="334" alt="image" src="https://github.com/user-attachments/assets/65997a02-ad2a-4d4b-a960-d2e6587f2a8a" />

(link for full details: <link>https://tryhackme.com/room/networksecurityessentials<link>)

## What will I be doing?

### Investing the logs and answering the questions.

As a SOC Analyst, analyzing logs manually can become a tedious task if the log files are large. Therefore, a Splunk instance is also provided in the VM if you decide to use it for log Analysis. 

To proceed, open the link localhost:8000 in the browser, click on the Search & Reporting tab on the left bar, and start analyzing the logs. Logs are pre-ingested into the index="network_logs".

Q1) Examine the firewall logs. What external IP performed the most reconnaissance?

I will be searching index="network_logs" in splunk. It found 2,485 events. 

<img width="1042" height="329" alt="image" src="https://github.com/user-attachments/assets/f00225d5-27ec-4bb4-ba41-264faed20b3e" />

- click on sourcetype on left sidebar where 3 types of logs are listed and will click on firewall_logs, there are 1,284 events.

<img width="1036" height="400" alt="image" src="https://github.com/user-attachments/assets/0dec6723-495e-4667-8156-95b7cfcf2391" />

search index="network_logs" sourcetype=firewall_logs and click on src_ip on left sidebar

IP with highest count is the one that perfroms most reconnaossance.

=>> 203.0.113.45

Q2) In the firewall log, Which internal host was targeted by scans?

 Easy Method, search index="network_logs" sourcetype=firewall_logs 

- go to dst_ip on side bar and the result will be the IP with highest count.

<img width="1010" height="726" alt="image" src="https://github.com/user-attachments/assets/4186e3a5-38b8-49d0-bf50-39a3cc7db273" />

=>> 10.0.0.20

Q3) Which username was targeted in VPN logs?

Search index="network_logs" sourcetype=vpn_logs and go to username on left side bar.

=>> 

Q4) What internal IP was assigned after successful VPN login?



















