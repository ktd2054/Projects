# Benign (Challenge room to investigate a compromised host.)

## Room Machine

Before moving forward, deploy the machine. When you deploy the machine, it will be assigned an IP. Access this room via the AttackBox, or via the VPN at 10.64.135.130.
The machine will take up to 3-5 minutes to start. ll the required logs are ingested in the index win_eventlogs.

One of the client’s IDS indicated a potentially suspicious process execution indicating one of the hosts from the HR department was compromised. 
Some tools related to network information gathering / scheduled tasks were executed which confirmed the suspicion. 
Due to limited resources, we could only pull the process execution logs with Event ID: 4688 and ingested them into Splunk with the index win_eventlogs for further investigation.

## About the Network Information

The network is divided into three logical segments. It will help in the investigation.

### IT Department

- James
- Moin
- Katrina

### HR department

- Haroon
- Chris
- Diana

### Marketing department

- Bell
- Amelia
- Deepak


# TASKS TO INVESTIGATE 

## How many logs are ingested from the month of March, 2022?

==> Started Searching, to get total logs we have to enter index=win_eventlogs and change from 24 hrs to All time from dropdown box.

<img width="384" height="250" alt="image" src="https://github.com/user-attachments/assets/41c98918-4279-4f0d-937a-4dc2eadcc32e" />

## Imposter Alert: There seems to be an imposter account observed in the logs, what is the name of that user?

==> I have to find an imposter account that looks like a user with distinct characters.
Let's count by Username; found one, here a user has double name and closely investigating its different 

<img width="1091" height="451" alt="image" src="https://github.com/user-attachments/assets/602616cf-5bbe-43f4-bcae-4e93e4b66af0" />

## Which user from the HR department was observed to be running scheduled tasks?

==> According to question there are 3 users in HR department. And the question is related to task means process is created and while investigationg it was found.

<img width="1085" height="759" alt="image" src="https://github.com/user-attachments/assets/a8ab4787-041a-43b4-b450-db9fa50244ad" />


## Which user from the HR department executed a system process (LOLBIN) to download a payload from a file-sharing host.

==> I searched index and Hostname"*HR*" at first, then clicked to CommandLine on the left sidebar -> rare value because a payload means some thing that can be executed and went to search LOLBIN on google.
It redirected me to its webpage where I found lots of .exe files and compared to the list from the result i got in splunk.

<img width="572" height="577" alt="image" src="https://github.com/user-attachments/assets/d510615e-388a-4686-81a1-42f8af6c0b27" />

Now, i used that .exe file to searh fro logs: index=win_eventlogs HostName="*HR*" certutil.exe ; aha i found the username that matched the employee name form the HR department list.

<img width="978" height="545" alt="image" src="https://github.com/user-attachments/assets/6f6915e8-4fc2-4209-a1f7-d1d4ffc55388" />

## To bypass the security controls, which system process (lolbin) was used to download a payload from the internet?

==> Ofcourse, it is certutil.exe

## What was the date that this binary was executed by the infected host? format (YYYY-MM-DD)

==> From the above screenshot, 2022-03-04.

## Which third-party site was accessed to download the malicious payload?

==> Again URL from screenshot above, controlc.com


## What is the name of the file that was saved on the host machine from the C2 server during the post-exploitation phase?

==> There is a file name after URL and it is bengin.exe

## The suspicious file downloaded from the C2 server contained malicious content with the pattern THM{..........}; what is that pattern?

==> got to the full link https://controlc.com/548ab556

## What is the URL that the infected host connected to?

==>https://controlc.com/548ab556





























