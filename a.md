# 🛡️ Building & Configuring a SIEM using Microsoft Sentinel (Azure + M365)

This project demonstrates a **hands-on SOC lab** where a Windows VM is deployed in Azure, exposed to the internet, and monitored using **Microsoft Sentinel**.  
The goal is to ingest real Windows security logs and analyze them using **KQL**, simulating a real-world SIEM environment.

---

## ☁️ 1. Azure Account Setup

### 1.1 Create an Azure Free Account
- Sign up for an **Azure Free Account**
- Upgrade the subscription to **Pay-As-You-Go** (required for Sentinel & Log Analytics)

### 1.2 Verify Default Subscription
- Navigate to **Subscriptions**
- Confirm **Default Subscription** is active

![Default Subscription](https://github.com/user-attachments/assets/9b102f5a-5185-4ce8-b16c-aedfc5773615)

---

## 📦 2. Resource Group Creation

A **Resource Group** acts as a logical container for related Azure resources.

### Steps
- Search **Resource Groups**
- Click **Create**
- Select **Default Subscription**
- Provide:
  - Resource Group Name (e.g., `SOC-Lab-RG`)
  - Region (nearest location)
- Click **Review + Create → Create**

![Resource Group Creation](https://github.com/user-attachments/assets/1bb1198b-a1b6-40be-ad70-be4fcaa8bc07)

---

## 💻 3. Virtual Machine Deployment (Exposed to Internet)

This VM generates logs that will be ingested into the SIEM.

### 3.1 VM Basics
- Go to **Virtual Machines → Create**
- Configure:
  - Subscription: Default
  - Resource Group: SOC-Lab-RG
  - Image: Windows 10 / Windows Server
  - Authentication: Username & Password
  - Allow **RDP (3389)**

![VM Basics](https://github.com/user-attachments/assets/0a166920-4577-4537-ae7f-4e9e0c8a1497)

### 3.2 Disks
- Leave all settings as **default**

### 3.3 Networking & NSG Configuration 🔥

A **Network Security Group (NSG)** works as a **virtual firewall**.

- Under **Networking → Configure Network Security Group**
- Click **Create New NSG**
- Add **Inbound Rule**:
  - Source: Any
  - Destination: Any
  - Service: RDP
  - Action: Allow
  - Priority: 1000

![NSG Rule](https://github.com/user-attachments/assets/99cdc4d0-da15-406e-995d-e1ea9697fe20)

- Click **Review + Create → Create**

![VM Validation](https://github.com/user-attachments/assets/455c3f99-79b3-4df6-82ee-6fa1d0338a15)

---

## 🔑 4. Connecting to the VM via RDP

### Steps
- Copy the **Public IP Address**
- Open **Remote Desktop Connection**
- Connect using VM credentials

![VM Public IP](https://github.com/user-attachments/assets/e3a8a947-ae39-4eff-88b0-bee63cb39fa6)

![RDP Connection](https://github.com/user-attachments/assets/f34b4787-28ed-443c-923c-731f1a6803da)

---

## 🚫 5. Disable Windows Firewall (Lab Only)

⚠️ **For learning purposes only — never do this in production**

### Steps
- Press **Win + R → wf.msc**
- Open **Windows Defender Firewall Properties**

![Firewall Console](https://github.com/user-attachments/assets/6509688f-36fe-4972-87cb-ea792f0de4eb)

- Turn **Firewall OFF** for:
  - Domain
  - Private
  - Public

![Firewall Disabled](https://github.com/user-attachments/assets/caf2a323-6306-418e-8742-517a87471622)

This allows the VM to attract unsolicited traffic 🌐

---

## 📊 6. Log Analytics Workspace (Log Ingestion Layer)

Microsoft Sentinel requires a **Log Analytics Workspace**.

### Steps
- Search **Log Analytics Workspace**
- Click **Create**
- Provide:
  - Workspace Name (e.g., `SOC-Lab-Workspace`)
  - Resource Group: SOC-Lab-RG
  - Region: Same as VM
- Click **Review + Create → Create**

![Log Analytics Workspace](https://github.com/user-attachments/assets/bac1ae0d-a649-48c6-aeb3-0cb34c141bc6)

---

## 🧠 7. Microsoft Sentinel (SIEM Setup)

### Steps
- Search **Microsoft Sentinel**
- Click **Create**
- Select the created **Log Analytics Workspace**
- Click **Add**

![Sentinel Workspace](https://github.com/user-attachments/assets/3b4a551a-85e4-48e0-8ed4-258b70267260)

---

## 📥 8. Ingesting Windows Security Logs

### 8.1 Install Windows Security Events
- Go to **Sentinel → Content Hub**
- Search **Windows Security Events**
- Click **Install**

![Content Hub](https://github.com/user-attachments/assets/c7df2109-3609-4ecc-98ba-26150ad94026)

![Install](https://github.com/user-attachments/assets/9b3ea169-e124-483a-9ffd-3b7a152abac0)

---

### 8.2 Verify Logs on VM
- Inside VM:
  - Open **Event Viewer**
  - Navigate to **Windows Logs → Security**

![Event Viewer](https://github.com/user-attachments/assets/0eb0d59c-f347-4839-8796-712dd9e28606)

---

### 8.3 Configure Data Collection Rule (AMA)

- Sentinel → **Manage**
- Choose **Windows Security Events via AMA**
- Open **Connector Page**
- Click **Create Data Collection Rule**
- Select:
  - Subscription
  - Resource Group
  - VM
  - All Security Events
- Click **Review + Create**

---

### 8.4 Verify Agent Installation
- VM → **Extensions + Applications**
- Confirm **Azure Monitor Agent** is installed ✅
- verify data ingestion -> go to VM -> settings -> extensions+applications


<img width="1106" height="248" alt="image" src="https://github.com/user-attachments/assets/ae01ea58-c43c-421e-baab-3c1572efcaff" />


# Searching the windows logs using sentinel

- go to sentinel -> logs 

<img width="1259" height="360" alt="image" src="https://github.com/user-attachments/assets/ae07fd07-20db-4588-b27b-494b8fd7d5d6" />

---

## 🔍 9. Querying Logs in Microsoft Sentinel

### Steps
- Sentinel → **Logs**
- Switch to **KQL Mode**
- Run:

```kql
SecurityEvent
```

- select KQl mode and search SecurityEvent

<img width="937" height="722" alt="image" src="https://github.com/user-attachments/assets/04c30b2a-4602-4823-86b5-d51127fe6a5d" />

- data shown

-  search an Security Event 

<img width="674" height="559" alt="image" src="https://github.com/user-attachments/assets/b12720b4-0781-49de-9988-6a4115c0b29e" /
