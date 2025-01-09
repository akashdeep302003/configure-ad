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

- Turn on Virtual Machines
- Install Active Directory on DC-1
- Create Domain Admin User
- Join Client-1 to the Domain
- Set Up Remote Desktop Access
- Create and Test User Accounts: Generate multiple user accounts via PowerShell and verify login functionality.

<h2>Deployment and Configuration Steps</h2>
1. Created VMs 
<p>
<img src="https://i.imgur.com/fhnWzi2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>In the first step we create two virtual machines. First was the DC-1 which is the domain contoller with the OS windows serever, 2vcpus and 8GB of RAM. Second was the client-1 with the OS windows 10 Pro, 2vcpus and 8GB of Ram. Kept both the VMs turned on. 
</p>
2. Installing Active Directory 
<br />

<p>
<img src="https://i.imgur.com/EJ21GQ1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/XYnIjQs.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
    <img src="https://i.imgur.com/1ini4kl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>Now we Logged in to DC-1, installed Active Directory Domain Services (AD DS), and promote DC-1 as a Domain Controller for a new forest (e.g., mydomain.com) and after that we restartd dc-1 and logged back in as mydomain.com\labuser.
</p>
3. Created a Domain Admin User 
<br />

<p>
<img src="https://i.imgur.com/nJ7Kkik.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/AEYFSxB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
    <img src="https://i.imgur.com/2lj5sur.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>Now in dc-1 we opened Active Directory Users and Computers (ADUC) and created two Organizational Units: _EMPLOYEES and _ADMINS. Added a new domain admin user named jane_admin in _ADMINS and assigned them to the “Domain Admins” security group and then we Logged in as mydomain.com\jane_admin.
</p>
4. Joining client-1 VM to the domain(mydomain.com)
<br />

<p>
<img src="https://i.imgur.com/uJBsB9M.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/oo9UBvu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
    <img src="https://i.imgur.com/sIvXeDc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>First, we logged in to Client-1 as labuser, join it to the domain (mydomain.com), and then restarted the VM. After that, we verified its presence in ADUC under the _CLIENTS OU.
</p>
5.Setup Remote Desktop for Non-Administrative Users on Client-1
<br />

<p>
<img src="https://i.imgur.com/fahJkgx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>Now we logged in to Client-1 as mydomain.com\jane_admin and enabled remote desktop access for domain users via system properties. This allows non-administrative users to log in remotely.
</p>
6.Creating Additional Users and Test Login
<br />

<p>
<img src="https://i.imgur.com/w8Ft8Np.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/a8tGRPX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
  <img src="https://i.imgur.com/fmrZHZb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>

</p>
<p>Logged in to DC-1 as jane_admin, used PowerShell to create multiple new users, and confirm their presence in the _EMPLOYEES OU via ADUC. Also, we test logging into Client-1 with one of these newly created accounts.
  Like in this case the user was bak.huj that we were successfully able to login.
</p>
<br />
