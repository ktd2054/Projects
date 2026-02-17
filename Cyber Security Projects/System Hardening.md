# System Hardening

## Linux Hardening

- Os: Kali Linux
- Tool: Lynis - a security audit tool for kali/linux systems.
- 

### Steps for Kali linux hardening

- update & upgrade the system

---
##### ** I got an error **

<img width="856" height="164" alt="image" src="https://github.com/user-attachments/assets/95fc85f0-b201-4e0f-a0f5-5ce2361e7349" />

##### How to fix it?

https://askubuntu.com/questions/591855/how-can-i-fix-e-sub-process-usr-bin-dpkg-returned-an-error-code-2

- After careful review of the link above, I got that I have to configure dpkg in root mode.
- To configure that i have to delete the file shown in the image above and create the file again to configure dpkg settings.
  
<img width="1007" height="722" alt="image" src="https://github.com/user-attachments/assets/9041be88-7593-46a9-ad12-475fa2ea66ce" />

- fixed the problem.
  
---
