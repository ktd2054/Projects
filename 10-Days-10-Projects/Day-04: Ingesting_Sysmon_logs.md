# 

## Installing Sysmon

- Download sysmon from Microsoft Sysinternals from https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
- extract the zip file and use powershell fro further configuration
- use sysmon config for further installation and install .xml file using Invoke-WebRequest command
  
<img width="944" height="902" alt="image" src="https://github.com/user-attachments/assets/f878dd37-8c86-4b6d-afe5-65fa320b0a5c" />

- check status of sysmon

<img width="617" height="209" alt="image" src="https://github.com/user-attachments/assets/bcab4ea3-8d76-4380-b2b6-b652431b53a3" />


### Generating Test Events

- first opening notepad application
- then pinging google.com

<img width="929" height="426" alt="image" src="https://github.com/user-attachments/assets/33b1de1b-8e0f-4aee-bf60-28c01f0d4bc2" />

### Checking Sysmonlog

- go to Win + R
- type in powershell: eventvmr.msc
- click on Applications and Services Log -> Epand Microsoft -> Look for Windows -> Scroll down for Sysmon and expand -> click on Operational 




