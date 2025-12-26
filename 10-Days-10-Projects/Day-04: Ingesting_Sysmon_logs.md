# Ingesting Sysmon Logs on Splunk Enterprise

### Generating Test Events

- first opening notepad application
- then pinging google.com

<img width="929" height="426" alt="image" src="https://github.com/user-attachments/assets/33b1de1b-8e0f-4aee-bf60-28c01f0d4bc2" />

### Verifying Sysmonlog

- go to Win + R
- type in powershell: eventvmr.msc
- click on Applications and Services Log -> Expand Microsoft -> Look for Windows -> Scroll down for Sysmon and expand -> click on Operational
- Check logs to find the event about notepad

![Image:](https://github.com/user-attachments/assets/bd2e7153-70bb-41b2-94d5-a75775031932)


### Starting Splunk 

-Windows VM

<img width="1181" height="139" alt="image" src="https://github.com/user-attachments/assets/efc07fb4-65e5-4fe8-9103-88535bf723fd" />



