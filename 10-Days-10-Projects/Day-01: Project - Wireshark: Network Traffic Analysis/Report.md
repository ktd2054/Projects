## Summary

This investigation analyzes a real-world packet capture (PCAP) obtained from malware-traffic-analysis.net to identify malicious and benign network activity. Using Wireshark, multiple analysis techniques were applied, including protocol review, traffic relationship analysis, TCP stream inspection, DNS analysis, and IOC extraction. While much of the observed traffic was legitimate enterprise background activity, confirmed malicious communication was identified and validated using threat intelligence sources.

## Investigative Process

### Step 1: Initial Traffic Overview

#### Observerd Protocols 
- TCP
- UDP
- DNS
- HTTP
- SMB

#### Observed Result

- TCP = 96.8% of packets, very high traffic; usually means applications, web, file access or authentication.
- TLS = 26.6% of packets, 83.75 of bytes; means larger data transfer, encrypted communication, few packets; might be normal or malware hidden
- Others including HTTP seems normal, DNS presebt but not dominant, SMB or SMB2 - indicates a real corporate network, ICMP conatins no ping flooding

### Step 2: Traffic Relationship Analysis

#### Observations

- Observation of IPV4 communications to identify communication patterns
- focus was IPs, Internal -> External Communications 
- several long duration sessions with moderate packet counts

#### Observed Results

- The primary internal host 10.6.13.133 was idenitifed communicating with many external IPs
- the multiple packet exhange was found over long durations which needs deeper investigation.
  
### Step 3: Following TCP Stream

---> What data's are actually being exchanged?

#### Observations

- Traffic associated with internal IP 10.6.13.133 was examined
- A TCP stream was isolated suing tcp.stream==69 to find and display isolated packets that belongs to TCP conversation.

#### Observed Results

- TCP stream analysis revealed encrypted communication TLSv1.3
- The client hello indicates SNI - edge-consumer.azureedge.net; suggesting communication with MS Azure CDN endpoint.


### Step 4: DNS analysis

#### Observations

- all dns traffic were reviewed
- dns queries from suspected host were isolated
- only dns response queries (intent) and query names were examined

#### Observation Results

- normal user browsing
- windows os background activity
- microsoft authentication & updates
- one dns-resolved domain/URL was found malicious confirmed via virus total


### Step 5: IOC Extractation

- Primary IP: 10.6.13.133
- External IP Addresses
- Domain Names
- URLs
- TLS metadata: SNI values
- Protocols

## Conclusion

A comprehensive network activity was conducted using a PCAP file from malware-traffic-analysis.com. The analysis included protocol review, conversation analysis, TCP stream investigation, DNS behaviour analysis and IOC extraction. This analysis of PCAP file has confirmed malicious activity. While several distinct streams were confirmed legitimate background traffic, attleast one URl associated was found and identified as malicious through threat intelligence. 


# Recommended Actions

- block malicious domain/url
- investigate host for infection
- Review additional PCAP streams for realted IOCs
- search SIEM for historical access to malicious URL

