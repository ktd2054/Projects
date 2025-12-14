
<img width="1498" height="523" alt="image" src="https://github.com/user-attachments/assets/eba0c637-234b-4209-89b9-b58108c7a50e" />

## Summary

- parent powershell.exe is exploited by attackers for executing scripts and downloading malicious payloads not only for admin tasks.
- nslookup.exe has been spawned which is unusual unless the system is troubleshooting DNS.
- It has encoded string in command;  RmYjEyNGZiMTY1NjZlfQ==  , which might contain malicious commands or data.
- domain-name seems suspicious;  haz4rdw4re.io
- It is originated from user downloads directory C:\Users\michael.ascot\downloads\
- The event code is 1 meaning Process Creation.

## Investigating the Alert

### Accessing SIEM Splunk

  index=* nslookup

#### Observations

- process execution nslookup.exe; domain names being queried haz4rdw4re.io suggesting potential malicious activity.
- nslookup.exe is originated from parent process powershell.exe which suggests the use of PowerShell scripts for automation
  of malicious activity.
- The process is operating from C:\Users\michael.ascot\downloads\ and C:\Users\michael.ascot\downloads\exfilteration which
  suggests that directory is being used to handle unauthorized data.
- All the events occured in short timeframe.
- Each execution of nslookup.exe uses a different encoded string.
- hostname affected by this is win-3450.


<img width="846" height="382" alt="image" src="https://github.com/user-attachments/assets/fa8f588f-0aa9-4e05-a7a8-ca977e494bf0" />


  
