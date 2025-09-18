# Severity: HIGH

This report has 5 cases of high severity phishing cases which are solved accordingly. 

# Case 1

<img width="1460" height="655" alt="image" src="https://github.com/user-attachments/assets/935bb3ea-e5d9-4a5f-80fc-1b2414687c15" />

This case is worth investigating as nslookup.exe has powershell.exe as parent rather than cmd. Assigning this task, I started my investigation using Splunk by searching events related to nslookup.exe. It showed 10 events related to the entered searching paramater.

<img width="1899" height="836" alt="image" src="https://github.com/user-attachments/assets/302b629e-03f6-4886-8dd0-0704c1bcaca9" />

Those 10 events have same process parent id which is 3728, so we now I will check the process parent id from the side bar. 

<img width="1196" height="764" alt="image" src="https://github.com/user-attachments/assets/2b283042-2995-442b-96c7-e1f4de8f119a" />

This will give me all the events realted to the id. When powershell was launched it seems there were other process too which were used to perform distinct activities. Now, lets search powershell and see the results. It displayed 68 events. 

<img width="1896" height="852" alt="image" src="https://github.com/user-attachments/assets/ef83431a-568b-4839-883a-e2438e328930" />

Let's jump into begining, 

<img width="1621" height="443" alt="image" src="https://github.com/user-attachments/assets/074a0a9f-4045-4d05-87d0-e174097a38b2" />

It seems the powershell was used to download the script named powercat.ps1, I will google powercat for the further details. 

<img width="1321" height="906" alt="image" src="https://github.com/user-attachments/assets/59785ca3-1a3f-47f4-8277-2f3d2a1c4493" />\

It looks like it is an exfiltraiton script used with Netcat & Ncat. 

# Case 2

# Case 3

# Case 4

# Case 5
