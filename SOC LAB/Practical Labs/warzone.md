# TryHackMe: Warzone 1 Write-Up

<img width="686" height="321" alt="image" src="https://github.com/user-attachments/assets/d4af53b8-9bde-49c0-a781-2f0afe62d1f3" />

## Task 1 - Your shift just started and your first network alert comes in.

You work as a Tier 1 Security Analyst L1 for a Managed Security Service Provider (MSSP). Today you're tasked with monitoring network alerts.

A few minutes into your shift, you get your first network case: Potentially Bad Traffic and Malware Command and Control Activity detected.  Your race against the clock starts. Inspect the PCAP and retrieve the artifacts to confirm this alert is a true positive. 

Your tools:

- Brim (https://tryhackme.com/room/brim)
- Network Miner (https://tryhackme.com/room/networkminer)
- Wireshark (https://tryhackme.com/room/wireshark)

Deploy the machine attached to this task; it will be visible in the split-screen view once it is ready.

If you don't see a virtual machine load then click the Show Split View button.

#### Answer the questions below

First, let's click start machine button <img width="70" height="32" alt="image" src="https://github.com/user-attachments/assets/b8ae34d0-d2da-4d67-8c52-c6438f45cddb" /> to start the target machine. Once, you get the IP Address of target machine, you can use Attack Box shown in upper left side of the room.

When AttackBox (Linux VM) is fully started, we need to open Zone1.pcap file from the desktop using Brim to analyse and investiagte the bad traffic. To find Brim, search using TryHackMe logo on the VM located on the top left corner <img width="80" height="32" alt="image" src="https://github.com/user-attachments/assets/ba3d785c-be9b-4e01-a1b9-b60d5343031f" />. When Brim app is opened use choose files button <img width="50" height="32" alt="image" src="https://github.com/user-attachments/assets/38dd52e8-7fd7-4577-b6c5-5f1017ec3a78" /> to select the given pcap file for further analysis. We need to wait few seconds to completely load the files.

<img width="1390" height="650" alt="image" src="https://github.com/user-attachments/assets/e4dfb707-9a12-4e6c-80cb-43f56b004dfe" />

Let's look at the available logfiles first to see what kind of data artefact we could have. Type <b><i> count() by _path | sort -r </i></b> in the search bar to find out distinct type of log files that we can rely on. (note*: to learn about the tools that we are using please follow the link under your tools section in Task 1 introduction.)

<img width="428" height="518" alt="image" src="https://github.com/user-attachments/assets/53046834-f511-4011-ae4d-db37f5a2a5a0" />

Let's review the frequently communicated host before starting the investigation. 

<b> Query:  cut id.orig_h, id.resp_p, id.resp_h | sort  | uniq -c | sort -r count <b>

The above query will sort the data and present originating host (source ip), responding port (destination port), responding host (destination host) in a tabular format. 

<img width="1017" height="460" alt="image" src="https://github.com/user-attachments/assets/2f1f9f19-86ae-442b-a429-63293e4262fb" />

The result provides sufficient information that helps us where to focus. Secodnly, Let's look at the port numbers and availabe services before narrowing our search. 

<img width="725" height="412" alt="image" src="https://github.com/user-attachments/assets/45e504cb-279e-4875-97a2-2e9e221dcd68" />

The above image represents the port numbers used by the number of services where http has the maximun number of records. 

Q1) What was the alert signature for Malware Command and Control Activity Detected?

To find an alert use query: <b> event_type == "alert" to find out the numbers of alerts and when you get the data scroll left to find the alert siganture colum for the given alert category. 

=> ET Malware MirrorBlast CnC Activity M3

<img width="932" height="575" alt="image" src="https://github.com/user-attachments/assets/e174d844-9073-4c6d-8f7d-65a54670fa6a" />

Q2) What is the source IP address? Enter your answer in a defanged format. 

It is easy to locate the source ip but to enter answer in defanged format navigate to CyberChef (https://cyberchef.org/) using the browser search. Once your page loads type Defang IP Addresses in the search bar and enter the source ip inside the input field. 

=> 172[.]16[.]1[.]102

<img width="1904" height="450" alt="image" src="https://github.com/user-attachments/assets/ab0e45f9-9afe-4eeb-9e7f-4d497fb270dc" />

Q3) What IP address was the destination IP in the alert? Enter your answer in a defanged format. 

Same as Q2 for destination IP.

=> 169[.]239[.]128[.]11

<img width="1516" height="500" alt="image" src="https://github.com/user-attachments/assets/866e64d5-f5dd-450c-89ac-c7feaf643280" />

Q4) Still in VirusTotal, under Community, what threat group is attributed to this IP address?

Go to VirusTotal website for ip investigation and type the destination ip address under search section and press enter. Here you go, it is suspicious. 
Now, click community for finding the threat group.

=> TA505

<img width="1412" height="600" alt="image" src="https://github.com/user-attachments/assets/d23ded4d-f336-48c9-b43c-cb43b1010d25" />

Q5) What is the malware family?

We can find it on same screenshot from Q4.

=> MirrorBlast

Q6) Do a search in VirusTotal for the domain from question 4. What was the majority file type listed under Communicating Files

First, let's find domain. Go to Relations tab on VirusTotal and look under Passive DNS Replication section. Bingo, the highest number of repliaction is our domain. 
Copy the domain and defang it in VirusTotal because according to Q4 it is defanged, at first I was also confused. Now, take the defanged URL to VirusTotal. Then, under relations-> communicaing files there is our answer. 

=> Windows Installer

<img width="1481" height="596" alt="image" src="https://github.com/user-attachments/assets/30cbd2d1-74b9-4640-9712-fdbd4c43efe0" />

Q7) Inspect the web traffic for the flagged IP address; what is the user-agent in the traffic?

To inspect web traffic use query: _path=="http" | cut user_agent to find the result.

=> REBOL View 2.7.8.3.1

<img width="648" height="695" alt="image" src="https://github.com/user-attachments/assets/f6d07aaa-c370-43be-85e9-efca556cc42f" />

Q8) Retrace the attack; there were multiple IP addresses associated with this attack. What were two other IP addresses? Enter the IP addressed defanged and in numerical order. (format: IPADDR,IPADDR)

Investigate by using query: _path=="http" and go to uri and user_agent column and look for something suspicious. And something is familiar in user_agent which is windows installer from Q6. 

=> 185[.]10[.]68[.]235,192[.]36[.]27[.]92

<img width="1511" height="458" alt="image" src="https://github.com/user-attachments/assets/75860594-d350-4f2a-be3e-826d227ceaf3" />

Q9) What were the file names of the downloaded files? Enter the answer in the order to the IP addresses from the previous question. (format: file.xyz,file.xyz)

One of the files can be seen in Q8 and for other one go left on same table from Q8. Bingo, we get both file names.

=> filter.msi,10opd3r_load.msi

<img width="1121" height="629" alt="image" src="https://github.com/user-attachments/assets/fb20ffe2-fb67-44f4-b6ff-9cb70f90687f" />

Q10) Inspect the traffic for the first downloaded file from the previous question. Two files will be saved to the same directory. What is the full file path of the directory and the name of the two files? (format: C:\path\file.xyz,C:\path\file.xyz)

Open pcap file in Wireshark. Search query: ip.addr == 185.10.68.235 and right click on first log. 
Go to Follow -> TCP Stream and search C:\, yay. (Note: When the file is opened check whether file name is correct or not.)

=> C:\ProgramData\001\arab.bin,C:\ProgramData\001\Action1_arab.exe


Q11) Now do the same and inspect the traffic from the second downloaded file. Two files will be saved to the same directory. What is the full file path of the directory and the name of the two files? (format: C:\path\file.xyz,C:\path\file.xyz)

Search query: ip.addr==192.36.27.92 and follow steps like Q10.

=> C:\ProgramData\Local\Google\rebol-view-278-3-1.exe,C:\ProgramData\Local\Google\exemple.rb

Thank you. Enjoy your shift. 
