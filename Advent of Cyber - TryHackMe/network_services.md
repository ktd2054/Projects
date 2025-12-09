# Network Discovery

### Scanning Whole Range

_nmap -p- --script=banner 10.67.171.123_

==> which attempts to retrieve the banner from a service running on a target host. 
Banners often contain information about the software version and other details that can be useful for reconnaissance.

<img width="549" height="213" alt="image" src="https://github.com/user-attachments/assets/ae906cf5-f589-4534-8d7a-affc34765413" />

Found some open ports

### Port 22/tcp – SSH (OpenSSH 9.6p1, Ubuntu 3ubuntu13.14)

- Service: SSH
- Banner: SSH-2.0-OpenSSH_9.6p1 Ubuntu-3ubuntu13.14

This tells:

- OS is likely Ubuntu
- SSH version is OpenSSH 9.6p1
- SSH is often a key entry point for brute-force or version-based CVEs.


### Port 80/tcp - HTTP

- http service, a website or web app

### Port 21212/tcp - trinket-agent

- uncommon, custom service may be CTTF, custom API

### Port 25251/tcp - 

- open, vsFTPd 
- a backdoor

#### and a TBFC application


-------------------------------------------------------------------------------------------------------------------------------------

==> To access ftp we need _ftp ip portno_


--------------------------------------------------------------------------------------------------------------------------------------


### Port Scan Modes

use of netcat (nc) will help to interact with network services,
_nc -v ip portno_


### TCP and UDP Ports

nmap -sU ip

if ports open,

dig @ip TXT key3.tbfc.local +short


--------------------------------------------------------------------------------------------------------------------

### Listing listening ports 

_ss -tunlp_


