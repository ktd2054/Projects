#TryHackMe: Warzone 1 Write-Up

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

It is easy to locate the source ip but to enter answer in defanged format navigate to CyberChef using the browser search. Once your page loads type Defang IP Addresses in the search bar and enter the source ip inside the input field. 

=> 172[.]16[.]1[.]102

<img width="1904" height="450" alt="image" src="https://github.com/user-attachments/assets/ab0e45f9-9afe-4eeb-9e7f-4d497fb270dc" />

