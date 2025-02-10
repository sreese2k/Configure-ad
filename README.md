# <p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Preapring Active Directory infrastructure in Azure
- Deploying Active Directory
- Creating Users with PowerShell
- Group Policy and Managing Accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://imgur.com/2n9mOWn.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this lab, we set up a Domain Controller (DC-1) and a Client (Client-1) in Azure to establish basic network communication. First, we created a Resource Group, then configured a Virtual Network with a Subnet to ensure both VMs were on the same network. We deployed DC-1 (Windows Server 2022), then set its Private IP address to static and disabled the Windows Firewall for testing. Next, we created  Client-1 (Windows 10) with the same credentials, attaching it to the same Virtual Network as DC-1. After deployment, we updated Client-1’s DNS settings to point to DC-1’s Private IP, then restarted the VM to apply the changes. Upon logging into Client-1, we tested connectivity by pinging DC-1’s Private IP, ensuring a successful response. Finally, running ipconfig /all in PowerShell confirmed that DC-1’s Private IP was correctly set as the DNS server, verifying proper network configuration and domain connectivity. 
</p>
<br />

<p>
<img src="https://imgur.com/0bQPvwP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We set up Active Directory (AD) on DC-1, created domain admin users, and joined Client-1 to the domain for centralized management. First, we installed Active Directory Domain Services on DC-1 and promoted it as a Domain Controller (DC) with the domain, mydomain.com. After restarting, we logged in as mydomain.com\labuser and used Active Directory Users and Computers (ADUC) to create Organizational Units (_EMPLOYEES and _ADMINS). We then added a new domain admin user, Jane Doe (jane_admin), and assigned her to the Domain Admins Security Group. After logging in as mydomain.com\jane_admin, we used this account for further administration. Next, we ensured Client-1 was set to use DC-1’s Private IP as its DNS, then logged in as labuser to join Client-1 to mydomain.com, triggering a restart. Finally, we logged into DC-1, verified Client-1 appeared in ADUC, created a new OU called _CLIENTS, and moved Client-1 into it, successfully completing the domain integration process.
</p>
<br />

<p>
<img src="https://imgur.com/Nik3Wsm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this lab, we configured Remote Desktop access on Client-1 for non-administrative users and created multiple domain accounts in Active Directory (AD). First, we logged into Client-1 as mydomain.com\jane_admin, enabled Remote Desktop for domain users through System Properties, and allowed non-admin users to connect remotely. Then, we logged into DC-1, used PowerShell_ise as an administrator, and ran a script to bulk-create users in the _EMPLOYEES Organizational Unit (OU). After verifying the accounts in Active Directory Users and Computers (ADUC), we successfully logged into Client-1 using one of the new users, confirming that domain authentication and Remote Desktop access were properly configured.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
