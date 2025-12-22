<img width="1786" height="575" alt="image" src="https://github.com/user-attachments/assets/f0fbbb8c-28d7-40c4-99a8-2703ea4d80c1" />

## Summary
## Investigation Process

### What is the IP address of the infected Windows client?

- applying filter http.request

<img width="1499" height="604" alt="image" src="https://github.com/user-attachments/assets/44f56cbc-3e92-4390-a5b6-29613622c990" />

- It seems our source is 10.1.17.215 where the IP seems to be making HTTP requests and downloading files.
  
### What is the mac address of the infected Windows client?

- after clicking and expanding Ethernet II where we will found source's MAC address.

<img width="1775" height="438" alt="image" src="https://github.com/user-attachments/assets/e9566ff4-989a-40b0-8682-f029573a346a" />

### What is the host name of the infected Windows client?

- filetring dhcp packets 
- clicking on dhcp request packet for analysis
- found the host DEKTOP-L8C5GSJ

<img width="1449" height="313" alt="image" src="https://github.com/user-attachments/assets/63239a7a-f82b-4320-80b1-2aac6bb59a21" />

### What is the user account name from the infected Windows client?

- to find user account name we need to analyse Kerberos authentication traffic as it is generated once a user logs in
- filtering kerberos.CNameString

<img width="1665" height="858" alt="image" src="https://github.com/user-attachments/assets/f6d179b4-720c-40f1-bd10-8ea63bfd7836" />

### What is the likely domain name for the fake Google Authenticator page?

- filtering dns && ip.address == 10.1.17.215
- found the fake page anmed authenticatoor.org

<img width="1794" height="527" alt="image" src="https://github.com/user-attachments/assets/a36c4ee2-06eb-408a-a026-932b980dfd32" />

### What are the IP addresses used for C2 servers for this infection?

- filtering ip source address ip.addr=1=10.1.17.215 to check the communications with other external IPs
- for HTTP based C2 ; http && ip.src==10.1.17.215
   <img width="1884" height="575" alt="image" src="https://github.com/user-attachments/assets/4302f432-47b8-4351-90bd-ae2b6f4c5658" />
   
- for HTTPS based C2
 <img width="1229" height="476" alt="image" src="https://github.com/user-attachments/assets/a2e44c6f-49df-4e04-8317-373813f2e00d" />

- for DNS based C2
<img width="1884" height="514" alt="image" src="https://github.com/user-attachments/assets/3dc4a2e0-3121-4038-ac96-11b19b6a07df" />

- for TLS based c2

<img width="1793" height="794" alt="image" src="https://github.com/user-attachments/assets/ad2bbf5f-2e5b-4b7a-b0e2-e7e95d128718" />

--------------
IPs found
--------------
5.252.153.241
-------------
45.125.66.32
-------------

## Conclusion



## References

----------------------------
| Topic/Files | Links/URLs
----------------------------
| PCAP | https://www.malware-traffic-analysis.net/2025/01/22/index.html
----------------------------
| Wireshark tutorials | https://wiki.wireshark.org/CaptureFilters


