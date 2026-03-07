# Severity: Medium

<img width="1450" height="605" alt="image" src="https://github.com/user-attachments/assets/2fdee855-f337-4ad1-9ce7-94bde0d39404" />

### Key Points

- alert triggered by an inbound email
- contains external links
- need to check whether any ednpoints ahve accessed those URLs
- need to check connections are blocked or not.

### What did I do.

- First, checked sender domain and it is malicious lets say fake microosft domain.

<img width="1179" height="536" alt="image" src="https://github.com/user-attachments/assets/83df0afa-88c8-4f32-bbaa-109f4b26f3bb" />

- Then, reviewed IP address as a part of OSINT ; came clean.

<img width="1449" height="525" alt="image" src="https://github.com/user-attachments/assets/91f55de5-e93d-4918-8ca5-5a35fe5ecc70" />

- Now, URL also came clean in TryDetectThis.

<img width="1475" height="562" alt="image" src="https://github.com/user-attachments/assets/7174d0b3-8d46-4126-b299-0bd556b7e0fa" />

- At last, using Splunk to check whether any endpoints have accessed the link or not. The result is positive.

<img width="1581" height="550" alt="image" src="https://github.com/user-attachments/assets/a973a151-38b2-412b-a607-119cd73c167e" />


### Report

<img width="1535" height="791" alt="image" src="https://github.com/user-attachments/assets/2535a4da-ab7f-4eb7-b055-2593883fce2f" />
