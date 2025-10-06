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

#### Act 2: Identifying the infected host and C2 server

- filtering the data using _dns_ query to identify host, c2 domain and suspicious query patterns.
  
<img width="1913" height="926" alt="image" src="https://github.com/user-attachments/assets/580f82fe-5305-4082-bcb2-1e5bf4b06d92" />

Results: 

- infected Host IP: 10.6.13.133
- DNS server (destination) IP: 10.6.13.3
- domain: massfriction.com

Now, checking the base domain _massfriction.com_ using virustotal.com and _urlscan.io_ to check whether it is malicious or not.

<img width="1621" height="949" alt="image" src="https://github.com/user-attachments/assets/a7965710-827f-4bf4-ae62-1dd8793884ca" />

Aha! It is malicious. 

Conclusion

<img width="706" height="133" alt="image" src="https://github.com/user-attachments/assets/b8ddc598-9d3d-4bc0-aec7-af67db564f16" />

#### Act 3: Indicator of Compromise

- finding C2 External IP by using domain _massfriction.com_, and the filter query is:

dns.qry.name contains "massfriction.com" and dns.flags.response == 1

<img width="1860" height="516" alt="image" src="https://github.com/user-attachments/assets/ac3550ec-f84f-4387-a7da-3900f44a3a63" />

Result:

<img width="445" height="100" alt="image" src="https://github.com/user-attachments/assets/09ff45d0-227c-47d7-a345-2bd49004ca2a" />

#### Act 4: Correlating TLS Traffic

- using query ip.addr == 10.6.13.133 and ip.addr == 10.6.13.3 and tls to check the relation between host and C2 IP for generation of
  huge TLS traffic

  

#### Case Report




