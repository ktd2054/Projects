# Tryhackme - Investigating with Splunk Write-up

<img width="1003" height="325" alt="image" src="https://github.com/user-attachments/assets/4306e931-1723-476b-b1db-900760677e2c" />

TryHackMe Room Link: https://tryhackme.com/room/investigatingwithsplunk

## Task 1 Investigating with Splunk

SOC Analyst Johny has observed some anomalous behaviours in the logs of a few windows machines. 
It looks like the adversary has access to some of these machines and successfully created some backdoor. 
His manager has asked him to pull those logs from suspected hosts and ingest them into Splunk for quick investigation. 
Our task as SOC Analyst is to examine the logs and identify the anomalies.

To learn more about Splunk and how to investigate the logs, look at the rooms splunk101 and splunk201.

### Room Machine

Before moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP Machine IP. 
You can visit this IP from the VPN or the Attackbox. The machine will take up to 3-5 minutes to start. 
All the required logs are ingested in the index main.



## Key Points in this investigation

- anamolius behaviours in tht logs of windows machine
- adversary has access of these machines and has created backdoor

Lets naviagte towards splunk -> searching & reporting 

#### How many events were collected and Ingested in the index main?

use command _index=main_  and change time to All time

<img width="793" height="341" alt="image" src="https://github.com/user-attachments/assets/b94d2b20-0964-484d-a5d8-1704f24ca2cc" />

=> 12256

#### On one of the infected hosts, the adversary was successful in creating a backdoor user. What is the new username?

to search for new account we need to search event id and it is 4720, 4722 or 4738.

_index=main EventID="4720"_

I got one event and while investigating it, I found new user section.

=> A1berto

<img width="888" height="365" alt="image" src="https://github.com/user-attachments/assets/18de1bbb-8fa4-4479-9cf3-edce42023bfb" />


#### On the same host, a registry key was also updated regarding the new backdoor user. What is the full path of that registry key?

for registry the event id will be 13. 

_index=main EventID=13 "A1berto"_

=> HKLM\SAM\SAM\Domains\Account\Users\Names\A1berto

<img width="848" height="295" alt="image" src="https://github.com/user-attachments/assets/8bbd455b-677f-4567-953f-4646472f262a" />


#### Examine the logs and identify the user that the adversary was trying to impersonate.

Above while examining new account creation we found it was A1betro and we can conclude that it is a fake account created for Alberto.
So, the adversary was trying to imporsonate was

=> Albetro

#### What is the command used to add a backdoor user from a remote computer?

Event id 4688 for searching command to add backdoor user or say process creation

_index=main EventID=4688_

- go to CommandLine on left side bar under Fields, if you cannot find click All Fields and check CommandLine
- look for new user creation or something similar and we also know what was the name of the user

 => C:\windows\System32\Wbem\WMIC.exe" /node:WORKSTATION6 process call create "net user /add A1berto paw0rd1"

<img width="807" height="441" alt="image" src="https://github.com/user-attachments/assets/96647494-0eec-449a-9af2-829cee0ba32f" />

#### How many times was the login attempt from the backdoor user observed during the investigation?

To check failed logon we have event id 4625.

_index=main "A1berto" EventID="4625"_

It shows 0 event.

=> 0

#### What is the name of the infected host on which suspicious Powershell commands were executed?

Search = index=main PowerShell Hostname | table _time Hostname 
and it will list hostname including time in a tabular format.

=> James.Browne

<img width="629" height="536" alt="image" src="https://github.com/user-attachments/assets/5a86f91e-2559-4104-b6d3-47efd5d8785a" />

#### PowerShell logging is enabled on this device. How many events were logged for the malicious PowerShell execution?

Go to google and search - event id for powershell activities about logging and powershell commands
You will get few options but choose the best one based on scenario, as powershell has been executed before so find realted to it.

_index=main EventID="4103"_

=> 79

#### An encoded Powershell script from the infected host initiated a web request. What is the full URL?

_index=main PowerShell_ and investiagte 

Copy the script

<img width="705" height="396" alt="image" src="https://github.com/user-attachments/assets/a6521149-b624-4e0e-8e00-2945cfb17962" />

Paste into cyber chef input section

Select FromBase64 and Decode Text [UTF-16LE (1200)] for receipe and bake it.

<img width="943" height="526" alt="image" src="https://github.com/user-attachments/assets/780e5863-6480-486c-b42d-4fed57a26b00" />

- select that above script highlighted (encoded value only) in the image and paste it again in input box.

- It will give you an ip address and add the end of the address /news.php highlighted in the 

- tryhackme little bulb on the question says to defang it so again use cyber chef.

<img width="1543" height="623" alt="image" src="https://github.com/user-attachments/assets/28f93ba9-2ef6-4116-8956-01417d31304f" />

=> hxxp[://]10[.]10[.]10[.]5/news[.]php

