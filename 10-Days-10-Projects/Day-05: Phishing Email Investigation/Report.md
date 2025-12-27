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
### Step -1 : Reading the email 

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

Where, 
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

Where,
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
### References 

- Getting started with awk, a powerful text-parsing tool. https://opensource.com/article/19/10/intro-awk
- Learn to use the Sed text editor. https://opensource.com/article/20/12/sed
- [https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/](https://www.cloudflare.com/learning/email-security/dmarc-dkim-spf/)












