# System Hardening

## Auditing Windows

- At first, search compliance toolkit microsoft using browser and click on the first link from microsoft.
- To download the appropriate toolkit we need to have he information about the os that we are using
- In my case it is windows server 2022, now lets download few things and i will explain about this first step.

<img width="1007" height="257" alt="image" src="https://github.com/user-attachments/assets/633feb51-2338-4aca-a2c5-3f196505cc12" />

- These downloaded files are tools that allows admins to download, analyse, test, edit and store microsoft-recommended security configuration baselines for windows and other microsoft products, while comparing them against other security configurations.

### Running Policy analyser toolkit

<img width="909" height="318" alt="image" src="https://github.com/user-attachments/assets/672cfdac-6ca3-41ef-b0f9-330e3707e6ac" />

- run as admninstrator

<img width="609" height="520" alt="image" src="https://github.com/user-attachments/assets/5878dbbf-dc8f-4986-b915-e02d9347fd6c" />

- click add, go to file and select add files from GPOs

<img width="728" height="358" alt="image" src="https://github.com/user-attachments/assets/fc36f9f3-fea4-44eb-9827-ccdfb343afd6" />

- the other file we downloaded before contains GPO folder

<img width="931" height="471" alt="image" src="https://github.com/user-attachments/assets/6969f9e8-adcd-4bb1-a0ed-fa9b9d4e46bc" />

- select that GPOs folder and click import then name the file name

<img width="500" height="270" alt="image" src="https://github.com/user-attachments/assets/7ff511fa-d29a-49ea-b8c3-c1e9ad276da5" />

- click on compare to effective state which compares to our recent policy.

<img width="975" height="436" alt="image" src="https://github.com/user-attachments/assets/8412f152-9b09-4cdd-a7c5-0b944e6000b7" />

- on effective state yellow color means the difference between current security state and effective state, as we clicked on each policy we can see everything in detail.

<img width="1183" height="352" alt="image" src="https://github.com/user-attachments/assets/942a7e4c-f37e-4fcf-b316-d1a1803fe1f9" />


### Lets apply and push some suggested policies 

- Now I will push that GGPo through domain controller.

- search for group policy management tool in domain

<img width="455" height="125" alt="image" src="https://github.com/user-attachments/assets/08e7866b-3caa-4d28-87e1-155efe4a48db" />

- creating a GPO named Logging Server and Workstation Policies
- right click and edit, click policies folder on sidebar
- go to windows settings -> security settings -> advanced audit policy configuration -> audit policies

- now lets perform one of the policies listed

<img width="959" height="98" alt="image" src="https://github.com/user-attachments/assets/71b4b881-04d5-4e69-b239-bef7bc439edb" />

- the top audit policy shown in above image states the credintinal validation is a conflit

- to push that policy we need to edit Credential validation under Account logon policy 

<img width="311" height="138" alt="image" src="https://github.com/user-attachments/assets/1c4672c8-91b6-437c-a4c7-e8f9cb457bc4" />

<img width="1229" height="623" alt="image" src="https://github.com/user-attachments/assets/2797cb2d-5428-4b81-8e26-12e722f4edf2" />



---
## Linux Hardening/Auditing

- Os: Kali Linux
- Tool: Lynis - a security audit tool for kali/linux systems.

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

## Installing lynis 

<img width="486" height="183" alt="image" src="https://github.com/user-attachments/assets/009f2509-7987-480f-861d-da0ff19641cd" />

## running lynis for audit 

<img width="795" height="359" alt="image" src="https://github.com/user-attachments/assets/394bce84-c4ae-413c-9d0e-ec6bbdad61a6" />

 - after running lynis for auditing, it will provide detailed description of settings to perform hardening in the sytem.
