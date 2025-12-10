# Investiagting With Splunk


---------------------------------------------------------------------------------------------------------------------
### Create a report from the network-server logs host that lists the ports used in network connections and their count.
#### What is the highest number of times any port is used in network connections?

=> i need data from host network server, and had to list all the ports and the highest number of times the port has been used.

index=* host="network_server" | stats count by port | sort count desc

<img width="877" height="673" alt="image" src="https://github.com/user-attachments/assets/1d0f3237-8841-465c-b4d3-afdc0bd26b0c" />

---------------------------------------------------------------------------------------------------------------------
