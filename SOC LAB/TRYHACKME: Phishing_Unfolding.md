
# TRYHACKME: PHISHING UNFOLDING LAB

### Dashboard

As I entered the SOC Simulator on TryHackMe, I noticed several key sections. The Dashboard displayed all alerts, including open and closed ones. There was a SIEM tool for event monitoring and analysis, a virtual machine named Analyst VM for hands-on investigation, as well as sections for documentation, playbooks, and a case report list for tracking and reporting incidents.
  
<img width="1898" height="837" alt="image" src="https://github.com/user-attachments/assets/287b98fb-7132-4eb1-b5bd-e3799bc0b770" />

### Alert Queue

When I clicked on Alert Queue in the sidebar, I was redirected to a list of all current alerts on the system. An interesting observation was that each alert displayed its type (for example, phishing or process-related) and its severity level (such as low or high), which helps determine the criticality of the alert and prioritize response efforts. 

<img width="1886" height="771" alt="image" src="https://github.com/user-attachments/assets/56def3a0-ee81-4652-b4dd-840c05e9f6f9" />

### SIEM

### Analyst VM

### Documentation

### Playbooks

### Case reports

### Guide 

# Investigation of Alerts

### Alert ID-1000: Suspicious Email From External Domain

I went to the action column and assigned the alert to investigate. The details of the alert is shown in the image below:

<img width="1618" height="380" alt="image" src="https://github.com/user-attachments/assets/d5f26c0f-6f07-4bfb-a06e-fc41752ed36e" />

To investigate the alert further, I used company information section under Documentation tab from sidebar. It has listed all the employees nad their logged-in host machine. This allowed me to verify that the receipent of the phishing email, Miguel O'Donnel from Sales, was indeed a legitimate employee and that his device was active. 

Next, I checked for malicious element in the email by identifying time, specific asset and the sender domain for threat intel. The URL analysis status showed clean. 

<img width="662" height="644" alt="image" src="https://github.com/user-attachments/assets/7d67a9bc-b57b-48f4-a29f-39653538ef19" />

Further, I wrote a case report and submitted for security team to review it.

<img width="1623" height="777" alt="image" src="https://github.com/user-attachments/assets/14b31d1b-783f-46ca-872c-c4726db21b21" />






