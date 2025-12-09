## Introduction to SIEM

Security Information and Event Management system (SIEM) 

- security solution used by SOC Analyst.


### Logs

Multiple devices communicate through internet using routers and they generate logs of activities known as devices log sources which is helpful for identifying malicious activities. 

#### Types

a) Host-Centric 

==> captures events that occured within or related to host 
==> windows, linux and servers generates these logs

 - A user accessing a file
  -  A user attempting to authenticate.
    -  A process execution activity
     - A process adding/editing/deleting a registry key or value.
       - PowerShell execution
      
  b) Network-Centric

  ==> when the hosts communicate with each other or access the internet to visit a website.
  ==> firewalls, IDS/IPS, routers generates such logs

  - SSH connection
  - A file being accessed via FTP
  - Web traffic
 -  A user accessing the company's resources through VPN.
 -  Network file sharing Activity
  
