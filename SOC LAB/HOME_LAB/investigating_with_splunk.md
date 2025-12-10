# Investiagting With Splunk


## Creating Reports and Dashboard in Splunk
---------------------------------------------------------------------------------------------------------------------
### Create a report from the network-server logs host that lists the ports used in network connections and their count.
### What is the highest number of times any port is used in network connections?

=> i need data from host network server, and had to list all the ports and the highest number of times the port has been used.

index=* host="network_server" | stats count by port | sort count desc

<img width="877" height="673" alt="image" src="https://github.com/user-attachments/assets/1d0f3237-8841-465c-b4d3-afdc0bd26b0c" />

- click save as on the right top bar, name the report and click save.

---------------------------------------------------------------------------------------------------------------------

### Create a dashboard from the web-server logs that show the status codes in a line chart. Which status code was observed for the 
### least number of times?

=> i need data from host web server, and had to list all status_code data and sort them in descending order.

index=* host="web-server" | stats count by status_code |  sort status_code

<img width="1381" height="626" alt="image" src="https://github.com/user-attachments/assets/eb1d495d-ed86-4c83-a6e9-c89c91c7cc44" />

- save the report first.
- click on dashboards on left side of the menu bar.
- create new dashboard -> set name -> select classic type
- go to add panel
- click new from report in right
- select the log
- go to a sqaure box on right side above the table as shown in image below

<img width="490" height="313" alt="webslogs" src="https://github.com/user-attachments/assets/6303d464-d640-4c83-842e-ae629d0c4764" />


- select lines chart

<img width="673" height="336" alt="image" src="https://github.com/user-attachments/assets/6980f276-91d0-46fc-ab56-003f4fcb8939" />
