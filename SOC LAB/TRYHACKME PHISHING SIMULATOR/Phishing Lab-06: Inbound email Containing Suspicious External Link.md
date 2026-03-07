# Severity: Medium

<img width="1166" height="616" alt="image" src="https://github.com/user-attachments/assets/67989824-4d70-4bcf-b1b8-19c546f86ffc" />

### Key Points

- employee J Garcia received an email containing one or more external links.
- need to check firewall or proxy for any attemoted URLs access
- check the connection state (allowed or blocked)

### What I did?

- First, I confirmed the receivers company's HR department domain, its different than receiver in the email.

- Then, checked sender email domain in TryDetectThis and showed the domain is clean.
  <img width="1181" height="730" alt="image" src="https://github.com/user-attachments/assets/f966bad1-c6e4-4e7a-a331-7f9f22882460" />

- Now, performed OSINT for URLs found in email using TryDetectThis, came clean.
  <img width="1163" height="554" alt="image" src="https://github.com/user-attachments/assets/910c6158-74d0-4fba-8e44-a9e47280f3fc" />

- Last, to confirm whether any endpoints have tried to access the URLs or not using SIEM (Splunk). It seems there is not any firewall or proxy logs or HTTP request made.

<img width="1901" height="897" alt="image" src="https://github.com/user-attachments/assets/eca29faa-7c29-4023-8fa6-af437f38556c" />

- Now let's not check datasource email but others if there is any. But none.

<img width="1406" height="669" alt="image" src="https://github.com/user-attachments/assets/c7f60b2f-a61f-4b5d-bd95-4db4f3500af0" />

### Report

<img width="1471" height="741" alt="image" src="https://github.com/user-attachments/assets/d90dab32-de68-4003-80ac-453ec56ce4e2" />

