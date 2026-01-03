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


## Simple Mail Transfer Protocol [Port 25]

- Email delivery over the Internet involves four main components:

- MUA (Mail User Agent): The email client used by users (e.g., Outlook, Thunderbird).

- MSA (Mail Submission Agent): Receives outgoing emails from the MUA and checks them.

- MTA (Mail Transfer Agent): Transfers emails between mail servers over the Internet.

- MDA (Mail Delivery Agent): Stores the email so the recipient can retrieve it.

#### 📨 Flow:

- MUA → MSA → MTA → MDA → recipient’s MUA

- To move emails, specific protocols are used:

- SMTP → sending emails (MUA/MSA ↔ MTA)

- POP3 / IMAP → retrieving emails from the server

- SMTP (Simple Mail Transfer Protocol) works in cleartext and listens on port 25 by default. Because it’s unencrypted, tools like Telnet can be used to manually send emails by issuing commands such as HELO, MAIL FROM, RCPT TO, and DATA.

⚠️ Security note: Since SMTP transmits commands and message content in cleartext, traffic can be intercepted, which is why secure variants (like SMTPS or STARTTLS) are commonly used in real-world environments.


## Post Office Protocol 3 (Port 110)


- POP3 (Post Office Protocol v3) is used by an email client to download emails from a mail server (MDA). The client connects to the POP3 server on port 110, authenticates with a username and password, retrieves messages, and usually deletes them from the server after download.

- Because POP3 works in cleartext, tools like Telnet can be used to interact with it using commands such as:

- USER / PASS → authenticate

- STAT → show number and size of emails

- LIST → list available messages

- RETR → retrieve a message

- ⚠️ Security note: Credentials and email content are sent in cleartext, making POP3 vulnerable to interception.

- 📌 Limitation: POP3 is not ideal for using multiple devices, as emails are typically removed after download. For mailbox synchronization across devices, IMAP is preferred.

## Internet Message Access Protocol (port 143)

- IMAP (Internet Message Access Protocol) allows emails to stay synchronized across multiple devices. Actions like reading, deleting, or flagging messages are stored on the mail server (MDA) and reflected on all connected clients.

- IMAP typically listens on port 143 and requires authentication (e.g., LOGIN username password). Unlike POP3, IMAP:

- Keeps emails on the server

- Supports folders, flags, and read/unread states

- Works well with multiple devices and clients

- IMAP commands are tagged (e.g., c1, c2) so the client can match server responses. Common actions include listing mailboxes and examining the inbox.

- ⚠️ Security note: Standard IMAP sends credentials and commands in cleartext, making it vulnerable to interception. Secure variants like IMAPS (port 993) or STARTTLS are used in real-world environments to protect credentials and data.




