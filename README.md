<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2019
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Create two Virtual Machines through Azure: Domain Controller(DC-1) Windows Server 2019 and a Host computer (Client-1) Windows 10.
- Make sure Client-1 is on the same virtual network as DC-1.
- If using a Mac computer, run the Application Microsoft Remote Desktop and use the public IP Addresses to create a connection to both Virtual Machines.
- Using the Azure Portal, Set the DC-1 ipconfigurations to a Static IP address
- Ensure a connection from Client-1 to DC-1 by running command line and pinging the private IP Address of DC-1 from Client-1.
- If the ping fails, ensure the DC-1 Firewall inbound rules for ICMPv4(echo Request) is enabled.
- On DC-1, using the server manager, add roles and features and start the process to install Active Directory Domain Services.
- Create a name for the domain, can be anything you like, AAFES.com or Mydomain.com if you like a generic name.
- Finish the installation process of Active Directory and Promote it as a server, DC-1 will restart at the end of the installation.
- log back into DC-1 to allow the Windows Server software finish the installtion of Active Directory.
- On DC-1, using the Server Manager Dashboard, under 'Active Directory Users and Computers,' create two organizational units(_Employees & _Admins) under the domain.
- Create a new user in the "_Admins" organizational unit and set the user a member of the "Domain Admins"
- Sign out and sign back into the newly created Domain Administrator account using the domain prefix of AAFES.com\"username" and enter the password.
- Switch over to the Azure Portal for Client-1 and change the inherted DNS server to Custom and enter the Private Static IP Address of DC-1.
- Restart Client-1 and log in.
- Add Client-1 to the domain under settings > about > rename computer or add change its domain and click "Change"
- Enter the domain name and wait for the prompt to log in as an administrator to add to the domain.
- Enter the domain administrator user name and password to join Client-1 to the Domain.
- On Client-1, change the Remote Desktop Settings to allow other users to log onto Client-1 by adding "Domain Users" to the list of users.
- Ensure Client-1 has joined the domain by using DC-1 Server Dashboard under Users and Computers; Under the 'Computers' organizational unit you should be able to see Client-1 is listed.
- Optional, You can add users to _Employees tab manually or by running a script
- If you want to add domain users by running a script, run "Powershell ISE" as an administrator that creates user names and passwords under the "_Employees" organizational Unit.
- To Ensure the newly created domain users are able to log into Client-1, on DC-1, under "Users and Computers" in the domain, under the "_Employees" organizational unit, select any user and attempt to log into client-1 using their credentials.  

<h2>Deployment and Configuration Steps</h2>

<p><img width="1680" alt="Screen Shot 2023-10-11 at 9 46 21 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/05fd058f-4b19-4bb3-963e-c21ba34237e9">
  
Create two Virtual Machines through Azure: Domain Controller(DC-1) Windows Server 2019 and a Host computer (Client-1) Windows 10.

  
<img width="1680" alt="Screen Shot 2023-10-11 at 9 49 29 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/dd8484d9-3ffd-4098-9724-204f3ca0b1f4">


<img width="1680" alt="Screen Shot 2023-10-11 at 9 50 42 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/330b34cf-c883-4b98-9287-936ff776a9cd">

Make sure Client-1 is on the same virtual network as DC-1.

<img width="1680" alt="Screen Shot 2023-10-11 at 9 54 35 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/d981e36f-7ff2-4208-9937-ee81442199e9">


<img width="1680" alt="Screen Shot 2023-10-11 at 9 56 38 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/12b853b7-931b-4a9e-b0d0-0bd1013db84b">

If using a Mac computer, run the Application Microsoft Remote Desktop and use the public IP Addresses to create a connection to both Virtual Machines.

<img width="1680" alt="Screen Shot 2023-10-11 at 9 59 38 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/2f69c994-d4af-458f-a6df-b80e94c704e7">

Ensure a connection from Client-1 to DC-1 by running command line and pinging the private IP Address of DC-1 from Client-1.

<img width="1680" alt="Screen Shot 2023-10-11 at 10 00 42 PM" src="https://github.com/joshmadakorcc/configure-ad/assets/130338872/76c940e1-b8b9-4b89-8b01-abd7c0d40571">

If the ping fails, ensure the DC-1 Firewall inbound rules for ICMPv4(echo Request) is enabled.



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
