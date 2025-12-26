# Ingesting Sysmon Logs on Splunk Enterprise

Well, I've already setup Sysmon, Splunk and it's components on both kali and windows VM. Please find the link here:
- Click here for the lab details ... (https://github.com/ktd2054/Projects/blob/main/SOC%20LAB/HOME_LAB/Lab%2002%3A%20Setting_up_SOC_Splunk%20_lab.md))

### Generating Test Events

- first opening notepad application
- then pinging google.com
- opening other apps and using their features

<img width="929" height="426" alt="image" src="https://github.com/user-attachments/assets/33b1de1b-8e0f-4aee-bf60-28c01f0d4bc2" />

### Verifying Sysmonlog

- go to Win + R
- type in powershell: eventvmr.msc
- click on Applications and Services Log -> Expand Microsoft -> Look for Windows -> Scroll down for Sysmon and expand -> click on Operational
- Checking logs to find the event about notepad
- It's confirmed
  
<img width="929" height="426" alt="image" src="https://github.com/user-attachments/assets/bd2e7153-70bb-41b2-94d5-a75775031932" />


### Starting Splunk 

- Windows VM Verify Splunk is running

<img width="1181" height="139" alt="image" src="https://github.com/user-attachments/assets/efc07fb4-65e5-4fe8-9103-88535bf723fd" />


### Ingesting data 

- Save the Operational file from event viewer into the computer 

<img width="1529" height="389" alt="image" src="https://github.com/user-attachments/assets/1d4a26ff-7184-4e51-90b2-ec986e704e79" />

- go to splunk -> settings -> add data -> upload the file and click next
- and on set source type if we do not find XmlWinEventLogs:Sysmon then
- go to Apps on left top
- click manage apps and on right top click on browse more app
- search for Add-ons for Microsoft Windwos and add-ons for sysmon and install each respectively.
- after installation, refresh the browser and go to settings -> add data
- select the file thenc lick next and on set source type page search for XmlWinEventLog:Splunk

<img width="1652" height="653" alt="image" src="https://github.com/user-attachments/assets/adff9ef0-0156-46e9-addd-018002c1ea59" />

- select and click next
- create a index name on input settings page

<img width="1298" height="376" alt="image" src="https://github.com/user-attachments/assets/fced46f7-039f-4c92-b016-3e6130557ee6" />

- click review adn submit 

<img width="720" height="245" alt="image" src="https://github.com/user-attachments/assets/b5998227-2cf6-4613-aab8-735a3d5618e2" />

- click start searching button and it showed nothing

- i again tried from start still nothing
- then something clicked and i thought i failed

### Did I fail to get datalwinevent?

- after successfully uploading .evtx file but not getting any data in sysmon amd eme think what did i do wrong
- then i asked chatgpt with screenshot, it said sysmon doesnot directly read .evtx file

<img width="812" height="528" alt="image" src="https://github.com/user-attachments/assets/3d14229d-066d-4cf2-a15c-9cc03a6185bc" />

- after this immediately I saved the Operational Event Files into .xml format and re-uploaded the file saved in .xml
- It was hard to read and search files in format
- then i remembered that splunk can ingest csv, json, xml, zip and text or win event logs.
- At last I saved into .txt file and re-uploaded the file
- fianlly it worked for now


<img width="1835" height="756" alt="image" src="https://github.com/user-attachments/assets/1baac9e0-bd4b-46dd-bb3b-f19e70fd81fb" />



### References

- Sysmon. https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
- How do you want to add data? https://help.splunk.com/en/splunk-enterprise/get-started/get-data-in/9.4/how-to-get-data-into-your-splunk-deployment/how-do-you-want-to-add-data
- https://help.splunk.com/en/splunk-enterprise/get-started/get-data-in/9.4/how-to-get-data-into-your-splunk-deployment/assign-the-correct-source-types-to-your-data#fe2a63dd_998f_44da_9c20_5f51691b7d30--en__Assign_the_correct_source_types_to_your_data


