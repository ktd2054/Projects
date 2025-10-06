# TryHackMe: Juicy Details

<img width="760" height="164" alt="image" src="https://github.com/user-attachments/assets/db966d14-0345-4a8c-a748-3d42b9ff11a3" />

## TAsk 1: Introduction

﻿Introduction

                                      

You were hired as a SOC Analyst for one of the biggest Juice Shops in the world and an attacker has made their way into your network. 

Your tasks are:

- Figure out what techniques and tools the attacker used
- What endpoints were vulnerable
- What sensitive data was accessed and stolen from the environment
  
An IT team has sent you a zip file containing logs from the server. Download the attached file, type in "I am ready!" and get to work! There's no time to lose!

Answer the questions below

Are you ready?

Answer => I Am Ready!

## Task 2: Reconnaissance

Analyze the provided log files.

Look carefully at:

- What tools the attacker used
- What endpoints the attacker tried to exploit
- What endpoints were vulnerable

### Answer the questions below

1) What tools did the attacker use? (Order by the occurrence in the log)

Let's open the downloaded files at once.

<img width="1693" height="508" alt="image" src="https://github.com/user-attachments/assets/07aa72d9-f96c-460e-b9d7-ceb0b9e7dab5" />

Look at acess.log file for tools that is being used.

=> nmap, hydra, sqlmap, curl, feroxbuster

2) What endpoint was vulnerable to a brute-force attack?

One of the tools used is Hydra, so it will be used for brute-force attack. Use ctrl + F to find the hydra keyword. Look for the endpoint.

=> rest/user/login 

3) What endpoint was vulnerable to SQL injection?

SQLMap was used for probable sql injection, search in the file and find the endpoint.

=> /rest/products/search

4) What parameter was used for the SQL injection?

Look at the parameter after endpoint. It's q.

=> q

5) What endpoint did the attacker try to use to retrieve files? (Include the /)

Find feroxbuster line to look for a file tried to download by an attacker.

=> /ftp
