#TryHackMe: Warzone 1 Write-Up

<img width="686" height="321" alt="image" src="https://github.com/user-attachments/assets/d4af53b8-9bde-49c0-a781-2f0afe62d1f3" />

## Task 1 - Your shift just started and your first network alert comes in.

You work as a Tier 1 Security Analyst L1 for a Managed Security Service Provider (MSSP). Today you're tasked with monitoring network alerts.

A few minutes into your shift, you get your first network case: Potentially Bad Traffic and Malware Command and Control Activity detected.  Your race against the clock starts. Inspect the PCAP and retrieve the artifacts to confirm this alert is a true positive. 

Your tools:

- Brim
- Network Miner
- Wireshark

Deploy the machine attached to this task; it will be visible in the split-screen view once it is ready.

If you don't see a virtual machine load then click the Show Split View button.

#### Answer the questions below

First, let's click start machine button <img width="70" height="32" alt="image" src="https://github.com/user-attachments/assets/b8ae34d0-d2da-4d67-8c52-c6438f45cddb" /> to start the target machine. Once, you get the IP Address of target machine, you can use Attack Box shown in upper left side of the room.

When AttackBox (Linux VM) is fully started, we need to open Zone1.pcap file from the desktop using Brim to analyse and investiagte the bad traffic. To find Brim, search using TryHackMe logo on the VM located on the top left corner <img width="80" height="32" alt="image" src="https://github.com/user-attachments/assets/ba3d785c-be9b-4e01-a1b9-b60d5343031f" />. When Brim app is opened use choose files button <img width="50" height="32" alt="image" src="https://github.com/user-attachments/assets/38dd52e8-7fd7-4577-b6c5-5f1017ec3a78" /> to select the given pcap file for further analysis. We need to wait few seconds to completely load the files.

<img width="1390" height="650" alt="image" src="https://github.com/user-attachments/assets/e4dfb707-9a12-4e6c-80cb-43f56b004dfe" />









