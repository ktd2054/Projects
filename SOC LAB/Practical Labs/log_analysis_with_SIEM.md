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





  
