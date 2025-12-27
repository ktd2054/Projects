## Phishing Email Investigation + Malware triage

### Goal: To do an end-to-end email investigation and Map with MITRE ATT&K plus Essential Eight + NIST 2.0 Frameworks

> 🚨 **WARNING — EDUCATIONAL USE ONLY** 🚨  
>  
> <span style="color:red"><strong>This repository is intended strictly for educational, defensive security, and SOC analyst training purposes.</strong></span>  
>  
> The techniques, logs, and analysis demonstrated here are provided **solely to understand attacker behavior and improve detection, investigation, and incident response capabilities**.  
>  
> <span style="color:red"><strong>The author is NOT responsible for any misuse, illegal activity, or damage caused by applying the information in this repository.</strong></span>  
>  
> Use of this material for unauthorized, unethical, or malicious purposes is **strictly prohibited**.

### Tools Used

- Virtual Box
- Kali Linux
- Terminal
- Github
- grep
- awk
- sed

### To-do 1: Download a sample email 

- I found sample emails in github under this repository https://github.com/rf-peixoto/phishing_pot/tree/main/email
- I downloaded sample-100.eml file inside kali linux VM machine

### To-do 2: Rename the file and create folders

- renaming from sample-100.eml to case1_phishing_email.eml
  
<img width="415" height="91" alt="image" src="https://github.com/user-attachments/assets/d7df775f-34a5-40e7-b142-1cd2178040d2" />

- creating a proper case folders

<img width="698" height="39" alt="image" src="https://github.com/user-attachments/assets/61896579-70cd-4899-a17c-05ae86eec7dd" />

- moving the downloaded renamed file to newly created folder 

<img width="598" height="61" alt="image" src="https://github.com/user-attachments/assets/8f64862e-7f43-4ab5-8e2f-0195220d6fe6" />

- verifying the folders and files

<img width="361" height="276" alt="image" src="https://github.com/user-attachments/assets/f2c095b2-00f9-4b57-a295-4d3078c0a128" />


## Investigating Email

--- 
### Step 1 : Reading the email 
---
- Email files contains thousands of lines where headers usually should be in the first 100 lines
- the following command helps us for log analysis 

<img width="621" height="120" alt="image" src="https://github.com/user-attachments/assets/86b33b9e-7bcc-4105-9e5b-847672d1d5fd" />

#### Where, 

sed → stream editor which reads text line by line instead of opening the file

-n → don’t print everything by default

'1,120p' → print only lines 1 to 120

---
#### What to look in that email at first?

- From
- To
- Subject
- Message ID
- Received
- Attachments
  
---

### Extracting Only headers

<img width="1308" height="53" alt="image" src="https://github.com/user-attachments/assets/b7379739-3bf6-4f2f-8f15-4341043dce9f" />

#### Where, 
- awk : is a powerful text-parsing tool
- 'BEGIN{h=1} : set variable h=1 in header mode
- h{print} : if h is true print the line
- /^$/ : a blank line where headers end needs to be matched
- {h=0} : when blank link is found stop printing 

- Output: It contains sender info, mail server paths, authentication results and so on ....

<img width="630" height="264" alt="image" src="https://github.com/user-attachments/assets/16c8b13b-69e9-4992-b468-ea6cd9371cff" />

---

### Searching headers 

- lets filter out important header sections

<img width="1576" height="226" alt="image" src="https://github.com/user-attachments/assets/5da03b5c-a50e-4350-a14e-2cb012df0f0c" />

#### Where,
- grep : searches text
- -E : uses OR logic
- i : case-insensitive

#### Header Analysis Output

- Received from outlook.com domain
- There are three distinct Received: from domains
- Original Sender is dtrum.de (57.128.69.202)
- Authentication_Results is spf=none ; domain did not pass or publish SPF and it is not an authorized server with IP address
- From domain is serenitepure.fr and Reply-to domain is aichakandisha.com ; they mismatch which means if user clicks reply it goes to attackers inbox

---
### Step 2: URL extraction and Defang
---
- lets find links or urls attached in the email
  
<img width="667" height="123" alt="image" src="https://github.com/user-attachments/assets/4df748eb-37a9-4e4a-ab81-38d7a5700eff" />

#### Where,

- -Eoi : allows regex, print only match, ignore case
- 'https?:// matches http ot https
- [^"<> ]+ stops before quotes, spaces or HTML tags
- sort -u removes duplicates only unique

### Defanging URLs 

- to prevent accidental clicks, safe if needs to be shared

<img width="788" height="55" alt="image" src="https://github.com/user-attachments/assets/16418ad7-b31a-4673-93b2-66a54af0bc1f" />

#### Where, s|^https?://|hxxp://|

- ^ → start of line

- https?:// → matches http:// or https:// and Replaces with hxxp://

#### and Where s|\.|[.]|g

- Replaces every dot with [.]

- g → global

BEFORE 

<img width="632" height="120" alt="image" src="https://github.com/user-attachments/assets/020a79fd-a201-468f-a905-2adb65d53381" />

AFTER DEFANG

<img width="656" height="118" alt="image" src="https://github.com/user-attachments/assets/8524eea2-d5a2-4093-b22a-03cbb9027bcd" />

---
### Step 3: Social Engineering Analysis

---
<img width="594" height="59" alt="image" src="https://github.com/user-attachments/assets/9274f5a5-5f5c-48cb-95b5-859b1cc71794" />

#### The HTML findings indicates red flags and they are:

- Email has clickable images acting as hyperlinks
- link redirects to external tracking domain
  
<img width="1264" height="222" alt="image" src="https://github.com/user-attachments/assets/3cc9ba13-56d6-4f6b-b386-ac9b22229245" />

#### The email is a phishing attempt designed to redirect users to an external site via a tracking URL.

---
### Step 4: Final Verdict Report

#### Classification 

- The email is malicious - Phishing.

#### Evidences 

- SPF authentication shows spf=none
- From, Reply-to and Return-domains are mismatched
- Email originated from external server was realyed through Microsoft Infrastructure
- HTML has clickable image acting as hyperlink
- Link redirects to external tracking domain
- Email uses social engineering technique

#### Recommended Actions

- Block sender email address and associated domains
- Block identified URls
- Search for similar IOCs
- Notify affected users and organise awareness program
- Reset user credentials

----

### Step 5: Framework Mapping

---

#### MITRE ATT&CK

- ID: T1566 Phishing  ==> The email is used to get victim to click a link to interact
- Sub-techniques: T1566.02 Spearphishing Link

#### Essential Eight

- Phishing with link : MFA, User application hardening

#### NIST CSF 2.0

- Detect : identified phishing indicators in headers SPF none, domain mismatches and redirected link in HTML
- Respond : Block sender/domain/URl, reset credentials, notify users
- Recover : improve mail security controls, tune detections

### References 

- Getting started with awk, a powerful text-parsing tool. https://opensource.com/article/19/10/intro-awk
- Learn to use the Sed text editor. https://opensource.com/article/20/12/sed
- [https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/](https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/)
- Mastering Grep command in Linux/Unix: A Beginner's Tutorial https://www.digitalocean.com/community/tutorials/grep-command-in-linux-unix











