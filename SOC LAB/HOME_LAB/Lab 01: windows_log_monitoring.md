# Windows Log Monitoring

### Overview

- Setting up the lab network
- hardening and enabling windows logging
- sysmon installation
- scaning and brute-force RDP
- hunting of attack in event viewer
- creating a SOC report

### Objective:

# Lab Setup

## Tools: VMWare, Windows 10, Kali linux, Sysmon, Event Viewer ...

### Step 1: Preparing Windows as target by creating a new user and enabling RDP

- Why to create a new user and enable RDP?

  ==> To detect attacker behaviour we need to do some noisy activities to generate logs and attacker usually targets Remote Desktop Protocol.
  and user account must be created to generate brute-force attacks without messing real account.

#### 1.1 Creating a test user on Windows

Windows -> Computer Management -> Local users and groups -> users -> right click -> new user -> fill the details -> create

<img width="890" height="491" alt="image" src="https://github.com/user-attachments/assets/d303e9be-8951-47f4-907c-e040468ed1b4" />

#### 1.2 Adding lab user to Remote Desktop Users

Windows -> Run -> type systempropertiesremote -> check allow remote assistance connections to this computer -> select users -> click add -> type name to add user

#### 1.3 Eanbling RDP through Windows Firewall

Windows -> Run -> type wf.msc -> inbound rules -> find Remote Desktop - User Mode  (TCP-in) -> right click enable 

** Note ** 

### Step 2: Turning on Windows audit logging 

- This will show security logs to clearly show the attack. We will enable audit policies to force Windows to record the important events needed for detection.

#### 2.1 Configuration of Audit Policy

Windows -> Run -> type secpol.msc -> Security Settings -> Local Policies -> Audit policy and enable success and failure settings for the following:

Click on each from the list -> right click -> properties -> check success and failures both -> 

- Audit logon events
- Audit account logon events
- Audit account management
- Audit object access 
- Audit process tracking
- Audit logoff events

#### 2.2 Enabling Detailed Process creation

Windows -> Run -> gpedit.msc -> Computer Configuration -> Windows Settings -> Security Settings -> Advance Audit Policy Configuration
-> Audit Policies -> Detailed Tracking


### Step 3: Installing Sysmon

  Reference: https://medium.com/%40jamesrawlings0/install-sysmon-on-windows-190d2d417717

- Download Sysmon from Microsoft Learn  https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon
- Download a config file (SwiftOnSecurity) https://github.com/SwiftOnSecurity/sysmon-config

![Security](https://img.shields.io/badge/Error-EncounteredProblem-red)

Sysmon cannot find a config file due to typo error.

<img width="883" height="426" alt="image" src="https://github.com/user-attachments/assets/42bc79cf-29ae-4165-b993-de5c0fcc94ac" />

Sucessufully installed.

<img width="653" height="297" alt="image" src="https://github.com/user-attachments/assets/11332558-2faa-48c9-8d81-e2ccf0667cf9" />















