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
- From the Active Directory installation task, some random users should have been generated
- In DC-1 --> Start --> Enter Active Directory Users and Computers --> mydomain.com --> _EMPLOYEES
- Select a user you would like to use to login to Client-1
- Connect to Client-1 using Remote Desktop Connection
   - Start --> Search 'Remote Desktop Connection'
- Copy and paste Client-1's public IP address --> Login with random user
  - **Note:** password to these random users is Password1

  <img src="https://i.imgur.com/ADa1rMt.png" height="60%" width="60%" alt="Disk Sanitization Steps"/>

**3. On DC-1, in C:, create 4 folders: “read-access”, “write-access”, “no-access”, "IT Support"**
 - In DC-1 --> File Explorer --> This PC --> C: 
