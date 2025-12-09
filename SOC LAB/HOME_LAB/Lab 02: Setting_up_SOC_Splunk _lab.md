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
- Downloading .tgz file for linux

### Splunk Installation

- naviagte to download directory using terminal
- change your user mode to root
- type command _tar xvzf splunk-10.0.2-e2d18b4767e9-linux-amd64.tgz_ for uncompress and installation
  
<img width="1484" height="327" alt="image" src="https://github.com/user-attachments/assets/19764bb9-35b1-4cdb-8737-c42c67c10aac" />

After installation is complete a folder named "splunk" will be created.

- move the folder to opt _mv splunk /opt/_
- go to _cd /opt/splunk/bin_ folder
- run using command _./splunk start --accept-license_

It will ask to create an admin acccount and after account creation it provides a link to access it through browser.

<img width="1353" height="384" alt="image" src="https://github.com/user-attachments/assets/53f9987b-5901-4f09-b749-51a3e32655fd" />

### Accessing Splunk

naviagte to browser http://kali:8000 and use the credntials created.

<img width="1907" height="872" alt="image" src="https://github.com/user-attachments/assets/4df0c499-7408-46ad-9cdb-9067a8f12fc1" />

- Click on search & reporting

<img width="1903" height="717" alt="image" src="https://github.com/user-attachments/assets/9876e974-170c-4717-86d7-f0504702f5df" />

### Interaction with CLI

#### Comamnds

- splunk start ( to start server )
- splunk stop
- splunk restart
- splunk status
- splunk add oneshot ( add a single event to splunk index )
- splunk search ( to search data )
- splunk help

### Data Ingestion

- configuration of data ingestion is important

#### Splunk Forwarder

- It is used to ingest linux logs into splunk stance.

a) heavy forwarder

- it is used when we need to apply a filter, analyze or make changes to log source before forwarding it to destiantion.

b) universal forwarder

- it is a lightweight agent that gets installed o target host and main purpose is to send logs to splunk instance or to another
  forwarder.

- Download it from Splunk Website.

- use command _tar xvzf splunkforwarder-10.0.2-e2d18b4767e9-linux-amd64.tgz_ for uncompress
- move _mv splunkforwarder /opt/_
- naviagte to  _cd /opt/splunkforwarder_
- _./splunk start --accept-license_
- setup credintials and done

<img width="1550" height="705" alt="image" src="https://github.com/user-attachments/assets/905ca3cb-510e-40b9-bd24-1c4b3e71b2fb" />

### Configuring forwarder on linux

- login to splunk -> go to settings
- click forwarding and receiving
- click on configure receiving

<img width="1209" height="542" alt="image" src="https://github.com/user-attachments/assets/aba0a9eb-4693-484b-93a4-dfe47939b58a" />

- click new receiving port -> enter 9997 as a port number

<img width="1902" height="309" alt="image" src="https://github.com/user-attachments/assets/961e088f-148f-4ca8-b5a6-dd0c1ec842b6" />

#### Create an index

It will store all the receiving data.

- setting indexes -> click new index
- index name: linux_host
- click save

Continue in forwarder with command _./bin/splunk forward-server MACHINE_IP:9997_ which will lsiten to port 9997.

- we will send logs to monitor from /var/log/syslog file

<img width="617" height="173" alt="image" src="https://github.com/user-attachments/assets/394f8cc1-d31f-4ca2-a3ca-69b59f847007" />

### I got an error

I was using ./splunk add forward-server MACHINE_IP:9997 instead of actual ip such as 192.168.1.0:9997. Problem solved.

### Lets utlize logger utility

- lets create a test log

<img width="652" height="256" alt="image" src="https://github.com/user-attachments/assets/b6677bff-28be-4d58-958f-ea6f7f5fb4e4" />

- go to splunk  -> search index=""


## References

- https://tryhackme.com/room/splunklab
- https://help.splunk.com/en/splunk-enterprise/administer/install-and-upgrade/9.0/plan-your-splunk-enterprise-installation/installation-instructions
