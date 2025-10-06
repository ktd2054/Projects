# TryHackMe: Juicy Details

<img width="760" height="164" alt="image" src="https://github.com/user-attachments/assets/db966d14-0345-4a8c-a748-3d42b9ff11a3" />

## Task 1: Introduction

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

## Task 3: Stolen Data

Analyze the provided log files.

Look carefully at:

- The attacker's movement on the website
- Response codes
- Abnormal query strings

### Answer the questions below

1) What section of the website did the attacker use to scrape user email addresses?

Let's look for product review section. Yay, It's product review, after analysing some lines, there are something different user reviews.
<img width="1881" height="948" alt="image" src="https://github.com/user-attachments/assets/ea5cca14-c225-4610-8b5c-1e5f03db550b" />

=> product reviews

2) Was their brute-force attack successful? If so, what is the timestamp of the successful login? (Yay/Nay, 11/Apr/2021:09:xx:xx +0000)

Search hydra in file and look for error code by scrolling down, as I found 200 in one row which means success.

=> Yay, 11/Apr/2021:09:16:31 +0000

3) What user information was the attacker able to retrieve from the endpoint vulnerable to SQL injection?

Search sqlmap in access.log file and look for any credintials tag such as email and password.

=> email, password

4) What files did they try to download from the vulnerable endpoint? (endpoint from the previous task, question #5)

Search ftp on file, you will notice a filename.

=> coupons_2013.md.bak,www-data.bak 

5) What service and account name were used to retrieve files from the previous question? (service, username)

Go to vsftpd.log to check ftp files. It can be seen a succcessful download of a file. 

=> ftp, anonymous

6) What service and username were used to gain shell access to the server? (service, username)

Go to auth.log file and file most unsuccessful login attempts. We will find the user and service.

=> ssh, www-data
