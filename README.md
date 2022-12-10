<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Active Directory Deployed in the Cloud (Azure)</h1>
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

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users


<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/kXWYZu8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the virtual machine for the domain controller DC-1 and name the Resource Group to be made at the same time (AD-1)
</p>
<br />

<p>
<img src="https://i.imgur.com/ANm61t0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create the second VM (Client-1).
</p>
<br />

<p>
<img src="https://i.imgur.com/JLZCa2z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Choose the Vnet that was created with VM1 (DC-1). Ignore the name above. The above example should show (AD-1vnet).
</p>
<br />

<p>
<img src="https://i.imgur.com/MiBX0co.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open DC-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/b8ydNOh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on Networking on the left hand side.
</p>
<br />

<p>
<img src="https://i.imgur.com/zQvZ7Ik.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on the NIC (Network Interface Card).
</p>
<br />

<p>
<img src="https://i.imgur.com/lLAZiw2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Then click on IP Configurations on the left hand side.
</p>
<br />

<p>
<img src="https://i.imgur.com/xkKkTSu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on the IP Address in the middle where it says dynamic. 
</p>
<br />

<p>
<img src="https://i.imgur.com/CoGg9Yp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set the IP Address to static and save.
</p>
<br />

<p>
<img src="https://i.imgur.com/dgbCJsp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into Client-1 and ping DC-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/WRT7vf5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log into DC-1 and open Windows Defender Firewall.
</p>
<br />

<p>
<img src="https://i.imgur.com/Nz3O8E1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Sort Inbound Rules by protocol and enable ICMP Core Diagnostics Rules as seen above.
</p>
<br />

<p>
<img src="https://i.imgur.com/pv6qewu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Ping is succeeding.
</p>
<br />

<p>
<img src="https://i.imgur.com/auNsXSs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Add Roles and Features to install Active Directory.
</p>
<br />

<p>
<img src="https://i.imgur.com/zgyq1f8.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click Next until Server Roles then add Active Directory Domain Services.
</p>
<br />

<p>
<img src="https://i.imgur.com/Y1vvcdD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click next until finished and install.
</p>
<br />

<p>
<img src="https://i.imgur.com/ky30CkV.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next, click flag on top right corner to promote server to a domain controller.
</p>
<br />

<p>
<img src="https://i.imgur.com/AM7FwlW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Add a new forest.
</p>
<br />

<p>
<img src="https://i.imgur.com/IMQ1Chp.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click next through the prompts and enter a password when requested and continue to install.
<br />

<p>
<img src="https://i.imgur.com/iBBLZzy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Server will restart and you will have to login as a mydomain (or whatever domain name you chose) user.
</p>
<br />

<p>
<img src="https://i.imgur.com/AyEq2J7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open Active Directory User and Computers.
</p>
<br />

<p>
<img src="https://i.imgur.com/wVv2AJU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create a few Organizational Units.
</p>
<br />

<p>
<img src="https://i.imgur.com/7PstyMk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Admins and Employees created.
</p>
<br />

<p>
<img src="https://i.imgur.com/TW4UGQI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on admin and right click in the panel to create a new user.
</p>
<br />

<p>
<img src="https://i.imgur.com/VPqymtN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Create Jane Doe Admin User.
</p>
<br />

<p>
<img src="https://i.imgur.com/lp49HXG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Set password and uncheck "set password on next login" and "check password never expires" for this example.
</p>
<br />

<p>
<img src="https://i.imgur.com/hfO8bHh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click jane doe user and go to properties, members then click add.
</p>
<br />

<p>
<img src="https://i.imgur.com/h7CLdcq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Write domain and click check names.
</p>
<br />

<p>
<img src="https://i.imgur.com/pKDb5nG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Select Domain Admins and click okay.
</p>
<br />

<p>
<img src="https://i.imgur.com/D6zpzBa.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click apply.
</p>
<br />

<p>
<img src="https://i.imgur.com/8QM93Zw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Jane Doe is now a part of the domain admins security group and has admin permissions.
</p>
<br />

<p>
<img src="https://i.imgur.com/0aNBbyx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Logout of labuser and log back in as Jane Doe.
</p>
<br />

<p>
<img src="https://i.imgur.com/M39G3e4.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login as jane_admin.
</p>
<br />

<p>
<img src="https://i.imgur.com/SGM6JmT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Successfully logged in as jane_admin.
</p>
<br />

<p>
<img src="https://i.imgur.com/pzZR3RP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
We need to set Client-1's DNS to DC-1's private IP now. Navigate to DC-1 on Azure and retreive the private IP address.
</p>
<br />

<p>
<img src="https://i.imgur.com/mrRwsD9.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go to Client-1's NIC by going to Networking on the left and clicking Network Interface.
</p>
<br />

<p>
<img src="https://i.imgur.com/cIFR491.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on the NIC to the right of Network Interface in bold.
</p>
<br />

<p>
<img src="https://i.imgur.com/CqO8pxe.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on DNS Servers on the left, change from Inherit to Custom and paste DC-1's private IP. Make sure no spaces exist before and after the address and save.
</p>
<br />

<p>
<img src="https://i.imgur.com/pLQRm77.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Go back to Client-1 VM and restart to flush the DNS cache.
</p>
<br />

<p>
<img src="https://i.imgur.com/mq0nm3y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Log back into Client-1.
</p>
<br />

<p>
<img src="https://i.imgur.com/gyoB26T.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Use ipconfig /all command in Command Prompt to see what DNS server address is being used. (10.0.0.4) in this case. It was successful.
</p>
<br />

<p>
<img src="https://i.imgur.com/oIdGWEN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now right click the start menu and go to System.
</p>
<br />

<p>
<img src="https://i.imgur.com/zTyrFuw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on rename this PC.
</p>
<br />

<p>
<img src="https://i.imgur.com/mHPvpxq.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on change.
</p>
<br />

<p>
<img src="https://i.imgur.com/veo0K9E.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Change the domain name to mydomain.com and click okay and then fill in the login and password as shown.
</p>
<br />

<p>
<img src="https://i.imgur.com/1hre36w.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Login successful as jane_admin. Now restart.
</p>
<br />

<p>
<img src="https://i.imgur.com/i1q1JP5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now log back into Client-1 as jane_admin.
</p>
<br />

<p>
<img src="https://i.imgur.com/j8ZHV2N.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Right click start menu and go to system.
</p>
<br />

<p>
<img src="https://i.imgur.com/tcKvLMX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on remote desktop.
</p>
<br />

<p>
<img src="https://i.imgur.com/TeKYP66.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on "select users that can remotely access this PC".
</p>
<br />

<p>
<img src="https://i.imgur.com/ntvexvL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on add and type in domain users and check names, then click okay.
</p>
<br />

<p>
<img src="https://i.imgur.com/syJQPkC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Domain Users has been added. Now all domain users are allowed to log into this computer.
</p>
<br />

<p>
<img src="https://i.imgur.com/CrdPMgj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on start menu and then Windows Administrative Tools.
</p>
<br />

<p>
<img src="https://i.imgur.com/geLZvth.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Open DC-1 and go to start menu, then Active Directory Users and Computers.
</p>
<br />

<p>
<img src="https://i.imgur.com/nHtOS9z.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Click on mydomain.com, Users then Domain Users.
</p>
<br />

<p>
<img src="https://i.imgur.com/Pw9rlCl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
All created users get added to this group. Now any non administator can log in.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

