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
- Using the Azure Portal, Set the DC-1 iP Configurations of the Virtual NIC to a Static IP address
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

If the ping fails, ensure the DC-1 Firewall inbound rules for ICMPv4(echo Request) is enabled and try again.
<img width="1680" alt="Screen Shot 2023-10-11 at 10 01 21 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/1150be80-f873-41e1-af53-1ea7a1092a39">



<img width="1680" alt="Screen Shot 2023-10-11 at 10 02 22 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/376020ea-e2ca-44dc-a64f-56dae2174f12">


On DC-1, using the server manager, add roles and features and start the process to install Active Directory Domain Services.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 04 49 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/de479f29-1e96-4098-8d50-2bf8c57b9701">


Finish the installation process of Active Directory and Promote it as a server, DC-1 will restart at the end of the installation.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 06 03 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/490ad28c-d00a-498d-b530-9cca246df339">

Create a name for the domain, can be anything you like, AAFES.com or Mydomain.com if you like a generic name.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 08 00 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/7070d685-5539-4b6a-8980-b32256472278">


Using the Azure Portal, Set the DC-1 iP Configurations of the Virtual NIC to a Static IP address(10.0.0.4).


<img width="1680" alt="Screen Shot 2023-10-11 at 10 16 27 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/0a8bea19-7a8a-466b-9c53-4de843c96dac">


On DC-1, using the Server Manager Dashboard, under 'Active Directory Users and Computers,' create two organizational units(_Employees & _Admins) under the domain.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 17 22 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/708a34d9-6627-4262-8ebc-ebb294c428a6">


Create a new user in the "_Admins" organizational unit and set the user a member of the "Domain Admins." Sign out and sign back into the newly created Domain Administrator account using the domain prefix of AAFES.com\"username" and enter the password.



<img width="1680" alt="Screen Shot 2023-10-11 at 10 22 09 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/ae6b142e-2c97-4948-8ab3-ac973b6f1cf2">



Switch over to the Azure Portal for Client-1 and change the inherted DNS server to Custom and enter the Private Static IP Address of DC-1. Restart Client-1 and log in.



<img width="1680" alt="Screen Shot 2023-10-11 at 10 29 52 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/11a06c9d-ba83-4dee-aff0-0dd577a76f09">


Add Client-1 to the domain under settings > about > rename computer or add change its domain and click "Change." Enter the domain name and wait for the prompt to log in as an administrator to add to the domain. Enter the domain administrator user name and password to join Client-1 to the Domain.



<img width="1680" alt="Screen Shot 2023-10-11 at 10 33 38 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/0909e01d-e1fc-4977-90c5-eeadb45dcb52">


On Client-1, change the Remote Desktop Settings to allow other users to log onto Client-1 by adding "Domain Users" to the list of users.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 31 39 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/75e806b2-5765-4182-b08b-84b47f1a374e">


Ensure Client-1 has joined the domain by using DC-1 Server Dashboard under Users and Computers; Under the 'Computers' organizational unit you should be able to see Client-1 is listed.



<img width="1680" alt="Screen Shot 2023-10-11 at 10 34 20 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/cedcde61-a12e-45b7-88da-298cbf0f218f">


add domain users by running a script, run "Powershell ISE" as an administrator that creates user names and passwords under the "_Employees" organizational Unit. To Ensure the newly created domain users are able to log into Client-1, on DC-1, under "Users and Computers" in the domain, under the "_Employees" organizational unit, select any user and attempt to log into client-1 using their credentials.


<img width="1680" alt="Screen Shot 2023-10-11 at 10 34 37 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/0b9d6b36-824e-4840-bbed-894cecc05001">



<img width="1680" alt="Screen Shot 2023-10-11 at 10 38 32 PM" src="https://github.com/Marionjr/configure-ad/assets/130338872/5a54724e-60fe-490a-8be6-896b66bc4243">


