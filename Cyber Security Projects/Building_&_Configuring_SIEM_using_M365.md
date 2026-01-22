# Building & Configuring SIEM using M365.md

- creating and signing up an Azure free account
- updating to pay as you go model
- locating default subscription
  
<img width="1729" height="338" alt="image" src="https://github.com/user-attachments/assets/9b102f5a-5185-4ce8-b16c-aedfc5773615" />

- searching resource groups and creating a resource group under the default subscription

<img width="866" height="416" alt="image" src="https://github.com/user-attachments/assets/1bb1198b-a1b6-40be-ad70-be4fcaa8bc07" />


# Create VM and exposing it to internet

- Basics

<img width="956" height="667" alt="image" src="https://github.com/user-attachments/assets/0a166920-4577-4537-ae7f-4e9e0c8a1497" />

- Disks : leave default

- Networking -> go to Configure network security group -> click create new

  #### It is a Virtual firewall which helps to control traffic.

- Under Inbound rules -> click Add an inbound rule

<img width="505" height="807" alt="image" src="https://github.com/user-attachments/assets/99cdc4d0-da15-406e-995d-e1ea9697fe20" />

- click review and create
- after successful validation pass -> click create

<img width="1368" height="282" alt="image" src="https://github.com/user-attachments/assets/455c3f99-79b3-4df6-82ee-6fa1d0338a15" />

- let's copy public IP address of VM and use RDP for connection

<img width="430" height="270" alt="image" src="https://github.com/user-attachments/assets/e3a8a947-ae39-4eff-88b0-bee63cb39fa6" />


## Connection via RDP

<img width="1013" height="679" alt="image" src="https://github.com/user-attachments/assets/f34b4787-28ed-443c-923c-731f1a6803da" />

- disabling windows firewall

- win + R -> search wf.msc

<img width="1063" height="422" alt="image" src="https://github.com/user-attachments/assets/6509688f-36fe-4972-87cb-ea792f0de4eb" />

- click windows defender firewall properties

- domain profile off

<img width="402" height="290" alt="image" src="https://github.com/user-attachments/assets/caf2a323-6306-418e-8742-517a87471622" />

- and so on for private and public profile
- click apply and ok
- let's wait until the created machine hits traffic

# Setting up SIEM

- before setting up SIEM; we need a workspace for log ingestions
- go to search -> log analysis workspace -> click create -> fill the details
- click review+create

<img width="861" height="736" alt="image" src="https://github.com/user-attachments/assets/bac1ae0d-a649-48c6-aeb3-0cb34c141bc6" />

- lets setup SIEM using sentinal

- search -> sentinal -> click

- click create and select the previous created SOC-Lab workspace

<img width="1196" height="404" alt="image" src="https://github.com/user-attachments/assets/3b4a551a-85e4-48e0-8ed4-258b70267260" />

- SIEM created

# Ingesting logs from previous web VM

- on sidebar under content management -> go to content hub

<img width="303" height="702" alt="image" src="https://github.com/user-attachments/assets/c7df2109-3609-4ecc-98ba-26150ad94026" />

- search secruity events and instll

<img width="743" height="752" alt="image" src="https://github.com/user-attachments/assets/9b3ea169-e124-483a-9ffd-3b7a152abac0" />

- go to RDP windows and search event viewer

- windwos logs-> security events

- ingesting that logs to our vm

<img width="1634" height="669" alt="image" src="https://github.com/user-attachments/assets/0eb0d59c-f347-4839-8796-712dd9e28606" />


- click on manage after successful installation of windwos security events

<img width="994" height="809" alt="image" src="https://github.com/user-attachments/assets/04f05da8-b01d-4cca-9688-a577dc22bf3e" />

- we will choose Windows security events via AMA

  <img width="1046" height="677" alt="image" src="https://github.com/user-attachments/assets/b69a82ee-ebfd-4559-8b35-49d43e737710" />


- click on open connector page

<img width="1254" height="902" alt="image" src="https://github.com/user-attachments/assets/948576c6-7189-41db-ad40-bd387da5b2ad" />

- under configuration -> click create data collection rule 

<img width="969" height="648" alt="image" src="https://github.com/user-attachments/assets/47dce3ba-155f-4b10-9c59-e5d79785e875" />

- creating rule

<img width="742" height="395" alt="image" src="https://github.com/user-attachments/assets/f3a2bdf1-058b-4464-ae30-22682836d153" />


- select subscription 

<img width="828" height="340" alt="image" src="https://github.com/user-attachments/assets/8ea402cd-f091-46ee-addc-8e74cb10d1d9" />

- click review+create and after validation click create 


- verify data ingestion -> go to VM -> settings -> extensions+applications


<img width="1106" height="248" alt="image" src="https://github.com/user-attachments/assets/ae01ea58-c43c-421e-baab-3c1572efcaff" />


# Searching the windows logs using sentinel

- go to sentinel -> logs 


<img width="1259" height="360" alt="image" src="https://github.com/user-attachments/assets/ae07fd07-20db-4588-b27b-494b8fd7d5d6" />

- select KQl mode and search SecurityEvent

<img width="937" height="722" alt="image" src="https://github.com/user-attachments/assets/04c30b2a-4602-4823-86b5-d51127fe6a5d" />

- data shown

-  search an Security Event 

<img width="674" height="559" alt="image" src="https://github.com/user-attachments/assets/b12720b4-0781-49de-9988-6a4115c0b29e" />

