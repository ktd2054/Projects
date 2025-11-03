# Conti - TryHackMe Write Up

<img width="751" height="236" alt="image" src="https://github.com/user-attachments/assets/e76f100a-5c24-4419-8817-7b913c141071" />

# Task 1 SITREP


# Task 2 Exchanged Server Compromised

Below are the error messages that the Exchange admin and employees see when they try to access anything related to Exchange or Outlook.

Task: You are assigned to investigate this situation. Use Splunk to answer the questions below regarding the Conti ransomware. 


#### Can you identify the location of the ransomware?

Searching index=* to get the all events data listed on. There are 28,145 events.

<img width="839" height="437" alt="image" src="https://github.com/user-attachments/assets/fba1ac0b-5eb8-4ec5-98e0-688dbb6b3363" />

Clicking _sourcetype_ on the left sidebar and after analysing it, clicking on WinEventLog: Microsoft-Windows-Sysmon/Operational as
it stores all the windows related events. Go to EventCode field, where we can see multiple id's

<img width="721" height="700" alt="image" src="https://github.com/user-attachments/assets/add51bb0-fdb2-498a-886d-58547aa32566" />

The eventid for file creation is 11. Click on 11 from EventCode Field.

<img width="855" height="392" alt="image" src="https://github.com/user-attachments/assets/7ee5c863-1f3e-4d02-b1be-637e53f9d317" />

Click on image field, if you do not find image field go to All Fields on sidebar, search the field name and tick the box.
Now, we can see the cmd.exe, an executable stored in a document folder.
<img width="721" height="546" alt="image" src="https://github.com/user-attachments/assets/b49ab3ae-a747-43bb-ae93-2db514ce8ccd" />


=> C:\Users\Administrator\Documents\cmd.exe

#### What is the Sysmon event ID for the related file creation event?

=> 11

#### Can you find the MD5 hash of the ransomware?

Clik on the storage link and add Hashes=* on searbar field and 1 event will pop-up.

<img width="1234" height="650" alt="image" src="https://github.com/user-attachments/assets/37be920b-9e64-4390-9107-e22b13d4854d" />

expand the event, and we will get the hash.

<img width="1245" height="663" alt="image" src="https://github.com/user-attachments/assets/4f4e65ae-fd8d-44f5-96c8-379cea6644f8" />

=> 290C7DFB01E50CEA9E19DA81A781AF2C


#### What file was saved to multiple folder locations?

use this command to search 
<img width="829" height="50" alt="image" src="https://github.com/user-attachments/assets/18b487d8-542f-4ee3-baf9-67127e374326" />

The file name is readme.txt

<img width="864" height="717" alt="image" src="https://github.com/user-attachments/assets/ea49b6b2-fa6b-46c9-ac6c-49173063f64a" />

=> readme.txt

#### What was the command the attacker used to add a new user to the compromised system?

<img width="713" height="469" alt="image" src="https://github.com/user-attachments/assets/c5ad59f4-82a2-4cc8-8400-6a12e6456332" />

search using the command in above image and will get a new user named securityninja added to the compromised system.

=> net  user /add securityninja hardToHack123$

#### The attacker migrated the process for better persistence. What is the migrated process image (executable), and what is the original process image (executable) when the attacker got on the system?

Click the hint on the question. It gives hint of event code 8. Use the below code.

index=* sourcetype="WinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=8
|  table SourceImage, TargetImage

<img width="1243" height="356" alt="image" src="https://github.com/user-attachments/assets/754b2c47-5481-4e41-8059-1ad5ea0206a0" />

where, table  = provies result in tabular format
SourceImage = file path of source process
TargetImage = file path of target process

=> C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe,C:\Windows\System32\wbem\unsecapp.exe

#### The attacker also retrieved the system hashes. What is the process image used for getting the system hashes?

Same process as above question. lass.exe where the dump password are stored.

<img width="1249" height="446" alt="image" src="https://github.com/user-attachments/assets/8c490e70-c82d-4674-9117-3e0a6a40bd4d" />

=> C:\Windows\System32\lsass.exe

#### What is the web shell the exploit deployed to the system?

Change the SourceType to IIS as it collects events related to webpages. Type index=* sourcetype=iis cs_method=POST 
|  search *.php* OR *.asp* OR *.aspx* OR *.jsp* where cs_method highlights the action taken by the client. go to sc_uri_stem

<img width="779" height="559" alt="image" src="https://github.com/user-attachments/assets/75341d29-49d5-461e-8280-2975bb7e00ce" />

=> i3gfPctK1c2x.aspx

#### What is the command line that executed this web shell?

Using search bar to find index=main sourcetype="WinEventLog:Microsoft-Windows-Sysmon/Operational" i3gfPctK1c2x.aspx and under CommandLine field on sidebar
<img width="875" height="594" alt="image" src="https://github.com/user-attachments/assets/d492d9f4-5aa2-4197-8dee-f9303b96e416" />

=> attrib.exe -r \\win-aoqkg2as2q7.bellybear.local\C$\Program Files\Microsoft\Exchange Server\V15\FrontEnd\HttpProxy\owa\auth\i3gfPctK1c2x.aspx

#### What three CVEs did this exploit leverage? Provide the answer in ascending order.

Research. 

=> CVE-2018-13374,CVE-2018-13379,CVE-2020-0796
