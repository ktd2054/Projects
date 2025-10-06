## Mini-Project 1: Network Analysis with Wireshark

### Objective: Analysing a real-world malware infected PCAP to identify the attackers activity. 

### Tools: Virtual Box, Kali VM, Wireshark

### Safety Tip

- using virtual host machines to protect physical computer
- verifying network settings and configured to host-only ensuring no connectivity

### Process

#### Step 1: navigating to malware-traffic-analysis.net using browser and downloaded the latest file from the top.

<img width="1333" height="914" alt="image" src="https://github.com/user-attachments/assets/d78ad996-5a92-47ab-8653-70609597ae85" />

#### Step 2: extracting the zip file and opening the file using Wireshark application for analysis.

<img width="1824" height="974" alt="image" src="https://github.com/user-attachments/assets/de4ad335-1673-4733-983a-c64bee0c8064" />

### Investigation

#### Act 1: Analyzing Baseline Statistics

- Analysing Statistics menu from the top bar to get information about common protocols and conversations between IP Addresses.

  Statictics -> Protocol Hierarchy

  <img width="1826" height="925" alt="image" src="https://github.com/user-attachments/assets/ddfe11b4-a7d9-440b-ac0e-b353ead9af23" />

  From the above data we get a lots of information about malicious activity. First, the TCP protocol has high number of suspicious
  session-based activity where DEC/RPC has lowest related to Windows Services. Likewise, the TLS, DNS, HTTP and SMB protocols indicates
  data exfiltration, beaconing and file access/transfer malicious activities.

