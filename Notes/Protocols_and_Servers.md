# Protocols and Servers

<img width="851" height="165" alt="image" src="https://github.com/user-attachments/assets/fd33ff9c-18c1-41f5-a50b-482efbc939c6" />


## Telnet (Port 23)

- The Telnet protocol is an **application layer** protocol used to connect to a virtual terminal of another computer.
- Using Telnet, a user can log into another computer and access its terminal (console) to run programs, start batch processes, and perform system administration tasks remotely.

#### Drawback of Telnet

- Anyone caputuring the network traffic will be able to discover usernames and passwords which will grant them to access the remote system

- type _telnet ipaddress_ for connection

## Hypertext Transfer Protocol (Port 80)

- Hypertext Transfer Protocol (HTTP) is the protocol used to transfer web pages.
- Web browser connects to the webserver and uses HTTP to request HTML pages and images among other files and submit forms and upload various files.

#### For http connection

- _telnet ipaddress 80_ is used to connect using http
- GET /filename HTTP/1.1
- host: telnet

## File transfer Protocol (Port 21)

- File Transfer Protocol (FTP) was developed to make the transfer of files between different computers with different systems efficient.
- FTP also sends and receives data as cleartext; therefore, we can use Telnet (or Netcat) to communicate with an FTP server and act as an FTP client

- type _telnet ipaddress 21_ for FTP connection

- FTP sends usernames, passwords, commands, and data in cleartext, making it insecure.
Because of this, simple tools like Telnet or Netcat can act as FTP clients by connecting to port 21 (FTP control channel).
 After logging in with USER and PASS, commands like SYST, STAT, PASV, and TYPE can be used to interact with the server.

- FTP uses two connections:

- Control channel (port 21) for commands

- Data channel for file transfers

- Active mode: data from server port 20

- Passive mode: data from a client port >1023

- File transfers cannot be completed via Telnet alone because FTP creates a separate data connection. Using a real FTP client (CLI or GUI), files can be listed and downloaded easily.

- ⚠️ Security note: Since everything is sent in cleartext, FTP traffic is easy to intercept and is a common target for attackers.





