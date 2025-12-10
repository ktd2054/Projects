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

### Search number of attempts 

index="linux-alert" sourcetype="linux_secure" ip
| rex field=_raw "^\d{4}-\d{2}-\d{2}T[^\s]+\s+(?<log_hostname>\S+)"
| rex field=_raw "sshd\[\d+\]:\s*(?<action>Failed|Accepted)\s+\S+\s+for(?: invalid user)? (?<username>\S+) from (?<src_ip>\d{1,3}(?:\.\d{1,3}){3})"
| eval process="sshd"
| stats count values(src_ip) as src_ip values(log_hostname) as hostname values(process) as process by username

### Search if access has been gained into the system


