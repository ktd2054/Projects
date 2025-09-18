# Severity: Low

## Suspicious child parent relationship

Assiging the task, 

<img width="1460" height="636" alt="image" src="https://github.com/user-attachments/assets/b157b01a-457d-49e0-a687-255beeb22605" />

Let's find out the relationship between services.exe and svchost.exe using SIEM. I am searching process id to find out
the events related to case.

<img width="1897" height="796" alt="image" src="https://github.com/user-attachments/assets/b43bf948-9a3e-49c3-9cd5-2f030c726f80" />

I could not find the exact event so, I added process name to find the event and bingo, here is the result.

<img width="1884" height="852" alt="image" src="https://github.com/user-attachments/assets/7eb6d817-1f2c-41fe-acc3-a9507aa59726" />

Let's reformat this using table query and here is the command, 

<img width="1364" height="472" alt="image" src="https://github.com/user-attachments/assets/bc6b79db-03db-481c-8c3c-27e910299f91" />

let's go back and query table view using process names and directory for analysing, 

<img width="1657" height="598" alt="image" src="https://github.com/user-attachments/assets/500d70bc-ffa1-475e-b036-5ebb67ccac16" />

After analysing, I am sure that this is False Positive because process svchost.exe having services.exe under the system directory is common. 

<img width="1400" height="573" alt="image" src="https://github.com/user-attachments/assets/f5e57817-ddd3-4bae-a68b-39e47c308d7c" />

Thank you.


