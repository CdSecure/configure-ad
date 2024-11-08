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

<h2>High-Level Deployment and Configuration </h2>

In this exercise, we will create a resource group containing a virtual network with two subnets. One subnet will host a Windows Server configured as a domain controller, and the other will host a Windows 10 client machine. We will then configure the Windows 10 computer to join the domain controlled by the Windows Server, allowing us to log in as a domain user.

<h2>Deployment and Configuration Steps</h2>

<p>

</p>
<br />

<p>

</p>
<p>
Creating a Resource Group in Microsoft Azure

Open the Azure Portal:

- Navigate to the Microsoft Azure portal and sign in with your credentials.
Create a New Resource Group:

- In the Azure portal, select Resource Groups from the left-hand menu or use the search bar at the top to find Resource Groups.
  
- Click on Add or Create to begin creating a new resource group.
Subscription: Ensure the correct subscription is selected.

- Resource Group Name: Enter a meaningful name for your resource group.
  
- Region: I choose US West 2 as the region for this exercise.
  
- Click Review + Create, then click Create to finalize the resource group creation.

<img width="689" alt="Screenshot 2024-11-08 at 3 36 43 PM" src="https://github.com/user-attachments/assets/51b72541-ce24-4a68-8a57-d1f895818bed">
  
</p>
<br />



<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
