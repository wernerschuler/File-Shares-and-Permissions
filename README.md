# File-Shares-and-Permissions

Requirements
-- 
Have the following setup:
- Active Directory running in Azure on a virtual machine (DC-1)
- A client machine running in Azure on a virtual machine (Client-1) and joined to the domain

Create some sample file shares with various permissions
--
**1. Connect to DC-1 as your domain admin account**
 - Go to portal.azure.com --> Virtual machines --> DC-1 --> Copy the public IP address
 - Start --> Search 'Remote Desktop Connection'
 - Paste DC-1's public IP address
 - Enter your domain admin account username and password

   <img src="https://i.imgur.com/qeaKw85.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**2. Connect into Client-1 as a normal user**
- From the Active Directory installation task, some random users have been generated
- In DC-1 --> Start --> Enter Active Directory Users and Computers --> mydomain.com --> _EMPLOYEES
- Select a user you would like to use to login to Client-1
- Connect to Client-1 using Remote Desktop Connection
   - Start --> Search 'Remote Desktop Connection'
- Copy and paste Client-1's public IP address --> Login with random user
  - **Note:** password to these random users is Password1

  <img src="https://i.imgur.com/ADa1rMt.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**3. In DC-1, in C:, create 4 folders: “read-access”, “write-access”, “no-access”, "IT Support"**
 - In DC-1 --> File Explorer --> This PC --> C: --> Right click --> New --> Enter name of folder

  <img src="https://i.imgur.com/k3bWZ3w.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**4.**

**5. Give Domain Users Read permisssion to "read-access" folder**
 - In DC-1 --> Right click read-access folder --> Properties --> Sharing --> Share
   
 <img src="https://i.imgur.com/6eUcXES.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>
   
 - Type domain users --> Add --> Share --> Done

  <img src="https://i.imgur.com/3En5uUi.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**6. Give Domain Users Read/Write permissions to "write-access" folder**
 - Right click the "write-access" folder --> Properties --> Sharing --> Share --> Type domain users --> Add --> Under Permission Level select Read/Write --> Share --> Done

   <img src="https://i.imgur.com/IgvXPFH.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**7. Give Domain Admins Read/Write permissions to "no-access" folder**
 - Right click the "no-access" folder --> Properties --> Sharing --> Share --> Type Domain admins --> Add --> Under Permission Level select Read/Write --> Share --> Done

<img src="https://i.imgur.com/dDuPpFu.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**8. For now skip the IT-Support folder**

**9. On Client-1, go to the share folder (dc-1)**
 - Go to Client-1 --> File explorer --> Enter in the search bar \\\dc-1

<img src="https://i.imgur.com/uPbOZWW.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**10. Try to access the folders you created**
 - You should not be able to access the "no-access" folder. A message like the image below should appear

<img src="https://i.imgur.com/V5KfrOB.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

 - You can access the "read-access" folder, but you cannot create anything inside of it

<img src="https://i.imgur.com/v6P3PeP.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

- In the "write-access" folder you can access this folder and create a folder inside of it

  <img src="https://i.imgur.com/VU1Ejli.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**11. Go to DC-1, create a security group in Active Directory called "IT-SUPPORT"**
 - In DC-1 --> Start --> Active Directory Users and Computers --> mydomain.com --> Right click --> New --> Organizational Unit
 - Name: _SECURITY_GROUPs
 - Refresh your domain:
   - Right click your domain --> Refresh
  - In _SECURITY_GROUPS --> Right click --> New --> Group
     - Group name: IT-SUPPORT
     - Group type: Security
  - OK

<img src="https://i.imgur.com/kBDUQ3e.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**12. On the "IT-Support" folder set the permissions, Group: "IT-SUPPORT", Permissions: Read/Write**
 - In DC-1 --> File explorer --> C: --> Right click the "IT-Support" folder
 - Sharing --> Share --> Enter IT-SUPPORT --> Add --> Below Permission Level select Read/Write --> Share --> Done

<img src="https://i.imgur.com/yfe8BLC.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**13. On Client-1 try to access the "IT-Support" folder. It should fail**
 - File explorer --> Enter \\dc-1 in the search bar --> IT-Support

<img src="https://i.imgur.com/koALC2R.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

  

     
   






