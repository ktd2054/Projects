# TryHackMe: Log Analysis With SIEM

#### Learning Objectives
Discover various data sources that are ingested into a SIEM.
Understand the importance of data correlation.
Learn the value of Windows, Linux, Web, and Network logs during an investigation.
Practice analysing malicious behaviour.

### Log Sources

- Host-Based Log Sources: brute-force attacks, unsuccessful logins, account mainpulation, malicious scripts, unauthorized access
  
- Network-Based Log Sources: external connection to unusual ports, unexpected logins and brute forces, port scanning
  
- Web-Based Log Sources: SQL injections, web shell exploitation

### Windows Logs

#### Sysmon

- malicious process execution
- suspicious network connection

#### WinEventLogs

- windows security logs
- windows system logs
  
## Lab Work 1: Windows Logs

- Practice Scenario

  You are an SOC Level 1 Analyst on shift and have received an alert indicating a suspicious network connection using port 
  5678 on the WIN-105 host. Your task is to conduct an investigation and determine whether this activity is suspicious.
  The logs for this task are located in the Splunk index task4. Use the following query: index=task4

  Lets login to Splunk. Clicking Searching & Reporting, searching index=task4

 Q)  Which IP address was the connection established with?
  
query: index=task4 EventCode=3 ComputerName=WIN-105 DestinationPort=5678 | table _time ComputerName Image SourceIp SourcePort DestinationIP DestinationPort

where, eventcode is 3 due to network related event and we can find computer name in the first log and destination port is given in our scenario
  
<img width="942" height="373" alt="image" src="https://github.com/user-attachments/assets/d22013e5-1cd8-4694-ad38-a85903e0c7c7" />

= 10.10.114.80

Q) Which process initiated this suspicious connection?

From the above screenshot, we can see image column.

= SharePoInt.exe

Q) What is the MD5 hash of the malicious process from the previous question?

query: index=task4 SharePoInt.exe |  table _time, Image, Hashes

= 770D14FFA142F09730B415506249E7D1

Q) What is the name of the scheduled task that was created on the system?

query: index=task4 EventCode=1 SharePoInt.exe
  |  table _time Image CommandLine ParentImage ProcessID

= Office365 Install

<img width="942" height="656" alt="image" src="https://github.com/user-attachments/assets/72590b05-c945-41c0-80e4-8904886c73c0" />


### Linux Logs

#### Authentication logs
  - Unusual Login Attempts: index=linux source="auth.log" *ubuntu* process=sshd | search "Accepted password" OR "Failed password"
  - Privilage Escalation: index=linux source="auth.log" *su* | sort + _time
  
#### System Logs
  - Persistence:index=linux sourcetype=syslog ("CRON" OR "cron") |  search ("python" OR "perl" OR "ruby" OR ".sh" OR "bash" OR "nc")

## Lab Work 2: Linux Logs

- Practice Scenario

You are an SOC Level 1 Analyst on shift and have received an alert indicating possible persistence through the creation of a new remote-ssh user on an Ubuntu server. 
Your task is to dive into the logs and determine exactly what happened on the system.
The logs for this task are located in the Splunk index task5. Use the following query: index=task5

Q) What was the timestamp of the remote-ssh account creation?
Answer Format Example: 2025-01-15 12:30:45

quey: index=task5 *remote-ssh*

= 2025-08-12 09:52:57

<img width="1280" height="640" alt="image" src="https://github.com/user-attachments/assets/14d96cb6-737e-4867-b09b-b39fd4d73241" />


Q) Which user successfully escalated their privileges to root prior to the action from the first question?

Click on All Fields in sidebar and tick user field and here we see our user

= jack-brown

<img width="1157" height="563" alt="image" src="https://github.com/user-attachments/assets/7ad169d8-7365-4d84-b0e9-27d2701c4f27" />

Q) From which IP address did the user from the previous question successfully log in to the system?

query: index=task5 source="auth.log" *ubuntu* process=sshd   | search "Accepted password" OR "Failed password"

<img width="1293" height="625" alt="image" src="https://github.com/user-attachments/assets/6f13405c-57bf-4a8d-9239-92ff2da2d71f" />

Q) How many failed login attempts occurred prior to this successful login?

query: index=task5 source="auth.log" *jack-brown* process=sshd   | search "Failed password" OR "Accepted password"

Total is 4 out of 6 listed in below image as on second last event it says message repeated 2 times so we exclude those 2.

= 4 

<img width="1285" height="844" alt="image" src="https://github.com/user-attachments/assets/bf6144de-b3d6-4a2d-a233-7754f3ae99d8" />

Q) Which port is the persistence mechanism configured to connect to?

query: index=task5 sourcetype=syslog ("CRON" OR "cron")

= 7654

<img width="1297" height="626" alt="image" src="https://github.com/user-attachments/assets/e680710f-2d09-4fc2-9121-bc8d4a90f95a" />


### Web Application Logs

#### Web Logs

- brute-force:
  index=* method=POST uri_path="/wp-login.php"
| bin _time span=5m
| stats values(referer_domain) as referer_domain values(status) as status values(useragent) as UserAgent values(uri_path) as uri_path count by clientip _time
| where count > 25
| table referer_domain clientip UserAgent uri_path count status

- web shell
index=*
| search status=200 AND uri_path IN(*.php, *.phtm, *.asp, *.aspx, *.jsp, *.exe) AND (method=POST AND method=GET)
| stats values(status) as status values(useragent) as UserAgent values(method) as method
  values(uri) as uri values(clientip) as clientip count by referer_domain
| where count > 2
| table referer_domain count method status clientip UserAgent uri
  
- DDoS

  index=* status=503
| bin _time span=10m
| stats values(referer_domain) as referer_domain values(status) as status values(useragent) as UserAgent values(uri_path) as uri_path count by clientip _time
| where count > 100000
| table _time referer_domain clientip UserAgent uri_path count status


### Lab Work 3:  Web Application Logs

- Practice Scenario

You are an SOC Level 1 Analyst on shift and have received an alert indicating a spike in activity on the organisation's web server.
Your task is to dive into the logs and determine exactly what happened.
The logs for this task are located in the Splunk index task6. Use the following query: index=task6


Q) Which URI path had the highest number of requests?

search index=task6 and got to url_path on sidebar

= /wp-login.php

<img width="1294" height="853" alt="image" src="https://github.com/user-attachments/assets/0d70298b-e51b-487a-be8d-20a8de21ac9c" />


Q) Which IP address was the source of the activity?

query: 
index=task6 method=POST uri_path="/wp-login.php"
| bin _time span=5m
| stats values(referer_domain) as referer_domain values(status) as status values(useragent) as UserAgent values(uri_path) as uri_path count by clientip _time
| where count > 25
| table referer_domain clientip UserAgent uri_path count status

= 10.10.243.134

<img width="1293" height="581" alt="image" src="https://github.com/user-attachments/assets/50794b54-1628-48d8-906e-5145d9d28803" />

Q) How can this activity be classified?

= Brute Force


Q) Which tool did the threat actor use?

<img width="1285" height="573" alt="image" src="https://github.com/user-attachments/assets/ec844b70-9fe8-470d-b95d-a784ff2095f2" />






