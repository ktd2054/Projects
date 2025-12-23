## Setting up AD Home Lab

 
## Objectives

1. Planning and understanding the home lab, choosing right IP, network type and AD components.
2. Downloading the required softwares namely VMware workstation pro, Windows 11 ISO and Windows Server 2022/2025 ISO
3. Creating a Virtual Machine for domain controller, member server and clients.
4. Configuration of VMware virtual networks, setting static IP for Domain Controller adnd understanding them.
5. Installing and promoting Domain Controller and AD DS.
6. Joining Computers to domain and applying basic Group policies
7. Testing and Troubleshooting DNS and connectivity, verifying authentication and domain logs.

## Installation of VMWare and Windows Server

### Screenshot of VMware after complete installation 

<img width="1682" height="552" alt="image" src="https://github.com/user-attachments/assets/07f57e9a-6dc9-4415-a971-ab1ce28ac002" />

### Screenshot of Windows Server 2022 after complete installation 

<img width="1375" height="810" alt="image" src="https://github.com/user-attachments/assets/c656bccc-3aeb-4219-821c-ec560135c988" />

### Things to do after installation

- Go to Local Server
- Change name for convienence
  
- Click on Ethernet () to maually configure IP -> right click on properties -> uncheck IPV6 -> double click IPV4 -> use the following IP address -> assign IP address -> set preferred DNS server

<img width="638" height="544" alt="image" src="https://github.com/user-attachments/assets/f59e693b-ee61-480d-a03c-31cb6c26ae25" />


### Adding Roles and Features

- Go to manage -> Add roles and features -> click next -> leave default for Installation type -> click next on server selection -> check Active Directory Domain Services -> add features -> next -> install

- go to flag symbol and check the instructions

- Click on promote this server to a domain controller

- check add a new forest -> add a domain name

- Set password and click next until reaching pre-requistics check.

- Click Install.

<img width="1500" height="645" alt="image" src="https://github.com/user-attachments/assets/e44844dc-68d9-4ac1-843c-36a6be5dc2ff" />


### Setting up windows server 2019 as destop experience to connect in same domain as our windows server 2022

- everything is same process but while assigning IP address the DNS should be as same as IP of windows server 2022


