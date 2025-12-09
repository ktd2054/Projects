## Introduction to SIEM

Security Information and Event Management system (SIEM) 

- security solution used by SOC Analyst.


### Logs

Multiple devices communicate through internet using routers and they generate logs of activities known as devices log sources which is helpful for identifying malicious activities. 

#### Types

a) Host-Centric 

==> captures events that occured within or related to host 
==> windows, linux and servers generates these logs

 - A user accessing a file
 -  A user attempting to authenticate.
 -  A process execution activity
 -  A process adding/editing/deleting a registry key or value.
 - PowerShell execution
      
  b) Network-Centric

  ==> when the hosts communicate with each other or access the internet to visit a website.
  ==> firewalls, IDS/IPS, routers generates such logs

 - SSH connection
 - A file being accessed via FTP
 - Web traffic
 -  A user accessing the company's resources through VPN.
 -  Network file sharing Activity


 ### Why SIEM?

<img width="733" height="729" alt="image" src="https://github.com/user-attachments/assets/74cd349f-b718-4ebd-b76f-480ab54caa5b" />

 
#### Features

- centarlized log collection from endpoints, servers, firewalls
- breaks all the different logs such as logs from windwos or linux into  different fields and presents in one consistent format.
- it correlates the logs of different sources and finds any relationship betweeen them.
- real-time alerts
- dashboards and reporting


### Log Sources and Ingestion

- Windows Machines -> event viewer
  
- Linux Machines
  
/var/log/httpd: Contains HTTP Request  / Response and error logs.

/var/log/cron: Events related to cron jobs are stored in this location.

/var/log/auth.log and /var/log/secure: Stores authentication-related logs.

/var/log/kern: This file stores kernel-related events.

- Web Server (/var/log/apache or /var/log/httpd.)


### Detection Rules

- The SIEM solution has detection rules that catches threats by correlating logs from the logs sources and trigger alerts.


### Alert Investigation

When monitoring SIEM, analysts spend most of their time on dashboards, as they display various key details about the network in a very summarized way. Once an alert is triggered, the events/flows associated with the alert are examined, and the rule is checked to see which conditions are met. Based on the investigation, the analyst determines if it's a True or False positive. Some of the actions that are performed after the analysis are:

Alert is a False Positive. It may require tuning the rule to avoid similar False positives from occurring again.

Alert is a True Positive. Perform further investigation.

Contact the asset owner to inquire about the activity.

Suspicious activity is confirmed. Isolate the infected host.

Block the suspicious IP.






