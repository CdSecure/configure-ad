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

- Next, we will create our own virtual network. In the Azure portal, search for Virtual Network, then create a new VNet by assigning it a name and ensuring it is in the same region as our resource group.

<img width="755" alt="Screenshot 2024-11-08 at 3 55 51 PM" src="https://github.com/user-attachments/assets/87da4a9e-315a-4223-808b-c234f2d27f1a">

Creating a Virtual Machine (VM) in Azure

We will now create our virtual machine (VM) within the resource group and virtual network (VNet) we previously set up.

1. Navigate to Virtual Machines:

- In the Azure portal, search for Virtual Machines and select it.
  
- Click on Add to start the VM creation process.

2. Configure Basic Settings:

- Resource Group: Ensure the VM is assigned to the resource group we created earlier.
  
- Virtual Machine Name: Provide a meaningful name for your VM.

- Region: Make sure the region matches that of your resource group (e.g., US West 2).

- Image: Select Windows Server 2022 Datacenter Azure Edition Hotpatch x64 as the operating system.
  
- Size: Choose a VM size with 2 or more vCPUs to meet the requirements.
  
- Administrator Account:
Username: Create a username for the VM administrator.
Password: Set a secure password and keep it accessible for future login.

3. Networking Configuration:

- Click on the Networking tab within the VM setup.
  
- Virtual Network: Ensure the VM is connected to the VNet we recently created.

- Subnet: Confirm that the VM is placed in the appropriate subnet within the VNet.
  
Review and Create:

- Review all the configurations to ensure they are correct.
- Click on Review + Create and then Create to deploy the VM.
  
5. Post-Creation:

- After the VM is deployed, keep your administrator username and password handy, as you will need them to log into the VM.

<img width="1183" alt="Screenshot 2024-11-08 at 4 12 05 PM" src="https://github.com/user-attachments/assets/184ec7cc-3ed8-4784-a61e-3f6bd096237e">
<br />
<img width="1184" alt="Screenshot 2024-11-08 at 4 15 27 PM" src="https://github.com/user-attachments/assets/08daecb7-abcf-4855-8e6b-4cfa501f7338">
<br />
<img width="1182" alt="Screenshot 2024-11-08 at 4 17 45 PM" src="https://github.com/user-attachments/assets/45af1317-6db7-4ed7-97b1-efb717ed52ba">

Creating the Windows 10 Virtual Machine

Now that the domain controller (Windows Server) is set up, create a Windows 10 VM in the same resource group and region:

1. Start VM Creation:

- Navigate to Virtual Machines in the Azure portal.

- Click Add to begin creating a new VM.


2. Configure Basics:

- Resource Group: Select the same one used for the domain controller.

- Region: Ensure it's the same as the domain controller's region.
VM Name: Choose a name for your Windows 10 VM.

- Image: Select Windows 10 Pro.
  
- Size: Pick a size with 2 or more vCPUs.
  
- Administrator Credentials: Set a username and password—remember these for later access.

3. Networking:

- In the Networking tab, select the same Virtual Network (VNet) you created earlier.
  
- Choose the appropriate subnet for the Windows 10 VM.
  
4. Review and Create:

- Verify all settings are correct.

- Click Review + Create, then Create to deploy the VM.

<img width="993" alt="Screenshot 2024-11-08 at 4 36 02 PM" src="https://github.com/user-attachments/assets/3b2348d9-7e0b-4c29-88d9-3420c25f3a1f">

<img width="991" alt="Screenshot 2024-11-08 at 4 41 46 PM" src="https://github.com/user-attachments/assets/4bfe1db6-9fd3-4d76-9428-e36f251640e5">


</p>
<p>

</p>
<br />
