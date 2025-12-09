# Splunk: Setting up a SOC Lab

Splunk is a SIEM solution that allows us to collet, analyze and correlate logs in a centralized server in real-time. 
This page documents installing Splunk on Linux/Windwos and configuring different log sources from both OS into splunk.

## Linux Lab

- Install Splunk on Ubuntu Server
- Install and integrate Universal Forwarder
- Collecting Logs from important logs sources/files like syslog, auth.log, audited, etc

## Windows Lab

- Install Splunk on Windows Machine
- Install and Integrate the Universal Forwarder
- Integrating and monitoring Coffely.THM's weblogs
- Integrating Windows Event Logs


## Splunk: Deployment on Linux Server

- creating an account in Splunk Enterprise
- Downlaoding .tgz file for linux

### Splunk Installation

- naviagte to download directory using terminal
- change your user mode to root
- type command _tar xvzf splunk-10.0.2-e2d18b4767e9-linux-amd64.tgz_ for installation
  
<img width="1484" height="327" alt="image" src="https://github.com/user-attachments/assets/19764bb9-35b1-4cdb-8737-c42c67c10aac" />

After installation is complete a folder named "splunk" will be created.

- move the folder to opt _mv splunk /opt/_
- go to _cd /opt/splunk/bin_ folder
- run suing command _./splunk start --accept-license_

It will ask to create an admin acccount and after account creation it provides a link to access it through browser.

<img width="1353" height="384" alt="image" src="https://github.com/user-attachments/assets/53f9987b-5901-4f09-b749-51a3e32655fd" />

### Accessing Splunk

naviagte to browser http://kali:8000 and use the credntials created.

<img width="1907" height="872" alt="image" src="https://github.com/user-attachments/assets/4df0c499-7408-46ad-9cdb-9067a8f12fc1" />

- Click on search & reporting

<img width="1903" height="717" alt="image" src="https://github.com/user-attachments/assets/9876e974-170c-4717-86d7-f0504702f5df" />

## References

- https://tryhackme.com/room/splunklab
- https://help.splunk.com/en/splunk-enterprise/administer/install-and-upgrade/9.0/plan-your-splunk-enterprise-installation/installation-instructions
