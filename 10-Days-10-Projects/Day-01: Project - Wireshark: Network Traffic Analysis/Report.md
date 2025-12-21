## Summary

## Investigative Process

### Step 1: Initial Traffic Overview

#### Observerd Protocols 
- TCP
- UDP
- DNS
- HTTP
- SMB

#### Observation Result

- TCP = 96.8% of packets, very high; usually means applications, web, file access or authentication.
- TLS = 26.6% of packets, 83.75 of bytes; means larger data transfer, encrypted communication, few packets; might be normal or malware hidden
- Others including HTTP seems normal, DNS presebt but not dominant, SMB or SMB2 - indicates a real corporate network, ICMP conatins no ping flooding

### Step 2: Traffic Relationship Analysis

#### Observations

- Conversation window


## Outcomes
