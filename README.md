
<p align="center">
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

- Setup both resources in Azure
- Ensure Connectivity between the Client and Domain Controller
- Install Active Directory
- Setup Remote Desktop for Users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/WvDgSfO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
For the first step I created the Domain Controller VM (Windows Server 2022) named “Dc-1". The virtual network (Vnet) will be created at this time. I then set the Domain Controller’s NIC Private IP address to be static. I created the Client VM (Windows 10) named “Client-1”. I used the same resource group and Vnet that were created before. Ensure that both VMs are in the same Vnet (checked the topology with Network Watcher). 

</p>
<br />

<p>
<img src="https://i.imgur.com/9VuvG37.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here I ensured connectivity between the client and the Domain Controller. I logged in to Client-1 with remote desktop and ping'd Dc-1's private ip adress using with ping -t 10.1.0.5. After I logged into Domain Controller on remote desktop and enabled ICMP v4 on local windows firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/TSuqYOp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here I installed Active Directory. On Dc-1 I clicked on Server Manager, clicked Add Roles and Features, clicked Active Directory Domain Services, and then Add Features. To finish installing Active Directory I added a new domain name "mydomain.com". Active Directory was successfully installed.
</p>
<br />

<p>
<img src="https://i.imgur.com/uqDaVZ7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Here I setup Remote Desktop for non-administrative users on Client 1. I logged into Client-1 as mydomain.com\chris_admin and opened system properties. I clicked Remote Desktop and allowed "domain users" access to remote desktop. Now I can log in Client-1 as a non-administrative user now. 

</p>
<br />
