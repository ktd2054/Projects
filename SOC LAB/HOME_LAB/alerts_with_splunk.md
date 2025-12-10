# Alerts With Splunk using TryHackMe

### Linux Host

<img width="532" height="412" alt="image" src="https://github.com/user-attachments/assets/4aff6a51-1713-49c3-a4b1-e968180f04f9" />

- two types of data fields must be in our interest : target host time and source IP
- if the ip is local that suggests if indeed it is an attacker they are already inside an orgainzation network
  
- search for both successful and failed login attempts, as well as events related to invalid users

command:

index="linux-alert" sourcetype="linux_secure" ipaddr | 
search "Accepted password for" OR "Failed password for" OR "Invalid user" | sort + _time 

<img width="1153" height="670" alt="image" src="https://github.com/user-attachments/assets/ad61af55-bc29-4ef2-8c3b-5a977be4f8bb" />


