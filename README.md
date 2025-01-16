<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>

Welcome to the first project in our Azure and Active Directory tutorial series. This foundational setup creates a simple lab environment in Azure, simulating a typical enterprise AD deployment. We’ll lay the groundwork needed for exploring how Active Directory is implemented and managed in real-world scenarios.

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration </h2>

In this exercise, we will create a resource group containing a virtual network with two subnets. One subnet will host a Windows Server configured as a domain controller, and the other will host a Windows 10 client machine. We will then configure the Windows 10 computer to join the domain controller allowing us to log in as a domain user.

<h2>Deployment and Configuration Steps</h2>

<b>&#9312;Creating a Resource Group in Microsoft Azure </b>

Open the Azure Portal:

- Navigate to the Microsoft Azure portal and sign in with your credentials.
Create a New Resource Group:

- In the Azure portal, select Resource Groups from the left-hand menu or use the search bar at the top to find Resource Groups.
  
- Click on Add or Create to begin creating a new resource group.
Subscription: Ensure the correct subscription is selected.

- Resource Group Name: Enter a meaningful name for your resource group.
  
- Region: I chose US West 2 as the region for this exercise.
  
- Click Review + Create, then click create to finalize the resource group creation.

<img width="689" alt="Screenshot 2024-11-08 at 3 36 43 PM" src="https://github.com/user-attachments/assets/51b72541-ce24-4a68-8a57-d1f895818bed">

- Next, we will create our own virtual network. In the Azure portal, search for Virtual Network, then create a new VNet by assigning it a name and ensuring it is in the same region as our resource group.

<img width="755" alt="Screenshot 2024-11-08 at 3 55 51 PM" src="https://github.com/user-attachments/assets/87da4a9e-315a-4223-808b-c234f2d27f1a">

<b>&#9313;Creating a Virtual Machine (VM) in Azure</b>

We will now create our virtual machine (VM) within the resource group and virtual network (VNet) we previously set up.

1. Navigate to Virtual Machines:

- In the Azure portal, search for Virtual Machines and select it.
  
- Click on add to start the VM creation process.

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
  
4. Review and Create:

- Review all the configurations to ensure they are correct.
- Click on Review + Create and then Create to deploy the VM.
  
5. Post-Creation:

- After the VM is deployed, keep your administrator username and password handy, as you will need them to log into the VM.

<img width="1183" alt="Screenshot 2024-11-08 at 4 12 05 PM" src="https://github.com/user-attachments/assets/184ec7cc-3ed8-4784-a61e-3f6bd096237e">
<br />
<img width="1184" alt="Screenshot 2024-11-08 at 4 15 27 PM" src="https://github.com/user-attachments/assets/08daecb7-abcf-4855-8e6b-4cfa501f7338">
<br />
<img width="1182" alt="Screenshot 2024-11-08 at 4 17 45 PM" src="https://github.com/user-attachments/assets/45af1317-6db7-4ed7-97b1-efb717ed52ba">

<b>&#9314;Creating the Windows 10 Virtual Machine</b>

Now that the domain controller (Windows Server) is set up, create a Windows 10 VM in the same resource group and region:

1. Start VM Creation:

- Navigate to Virtual Machines in the Azure portal.

- Click Add to begin creating a new VM.

2. Configure Basics:

- Resource Group: Select the same one used for the domain controller.

- Region: Ensure it's the same as the domain controller's region.

- VM Name: Choose a name for your Windows 10 VM.

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

<b>&#9315;Setting the Domain Controller's Private IP Address to Static</b>

 4) After creating the domain controller, we need to set its virtual network interface card (NIC) private IP address to static:

1. Navigate to the Domain Controller VM:

- In the Azure portal, go to the Virtual Machines section.
- Select the Windows Server VM that serves as your domain controller.
  
2. Access Networking Settings:

- In the left-hand menu of the VM, click on Networking.

3. Locate the Network Interface:

- Under the Network interface section, note the private IP address assigned to the domain controller.
- Click on the network interface name to access its settings.
  
4. Modify IP Configuration:

- In the network interface settings, select IP configurations from the left-hand menu.
- You will see the IP configuration labeled ipconfig1. Click on it to edit.
  
5. Change IP Assignment to Static:

- Under Private IP address settings, you will see Assignment set to Dynamic.
- Change the Assignment from Dynamic to Static.
  
6. Save Changes:
- Click Save to apply the changes.

<img width="1053" alt="Screenshot 2024-11-12 at 11 35 50 AM" src="https://github.com/user-attachments/assets/2d251fb7-415c-44b1-95e4-411e106b9c47">
<br />
<img width="1059" alt="Screenshot 2024-11-12 at 11 36 14 AM" src="https://github.com/user-attachments/assets/052c53b5-3ce2-4c17-a6f6-766b73efe4a6">
<br />
<img width="1055" alt="Screenshot 2024-11-12 at 11 36 38 AM" src="https://github.com/user-attachments/assets/ca2a1149-9ea5-4ee2-af16-2777c0c8ac86">
<br />
<img width="592" alt="Screenshot 2024-11-12 at 11 37 00 AM" src="https://github.com/user-attachments/assets/55cb1a34-e8f2-4ead-9061-a2c189056c5f">

<b>&#9316;Disabling the Windows Firewall on the Domain Controller</b>

Now that the private IP address is set to static, we will log into the domain controller and disable the Windows Firewall.

1. Log into the Domain Controller:

- Use Remote Desktop Protocol (RDP) to connect to your Windows Server VM (the domain controller).
  
- Enter the username and password you created earlier.
  
- Note: Upon logging in, the Server Manager should automatically open. If it doesn't, verify that you are connected to the correct VM in Azure.

2. Access the Windows Firewall Settings:

- Click on the Start button at the bottom left corner.
  
- Type Run in the search bar and select the Run application.
  
- In the Run dialog box, type WF.MSC and press Enter. This will open the Windows Defender Firewall with Advanced Security window.

3. Disable the Firewall for All Profiles:

- In the left pane, right-click on Windows Defender Firewall with Advanced Security on Local Computer and select Properties.
  
- You will see three tabs: Domain Profile, Private Profile, and Public Profile.
  
- Domain Profile Tab:
Set Firewall state to Off.
- Private Profile Tab:
Set Firewall state to Off.
- Public Profile Tab:
Set Firewall state to Off.

This ensures the firewall is disabled across all network profiles.

4. Apply the Changes:

- Click OK to save the settings and close the properties window.

<img width="1800" alt="Screenshot 2024-11-12 at 12 17 05 PM" src="https://github.com/user-attachments/assets/2822c696-e75f-4ad4-9357-2186bd06505e">

<img width="1800" alt="Screenshot 2024-11-12 at 12 17 43 PM" src="https://github.com/user-attachments/assets/3645b4e0-9335-4959-b6f3-4ad1eeadf7c2">

<img width="1800" alt="Screenshot 2024-11-12 at 12 17 58 PM" src="https://github.com/user-attachments/assets/58d6b87d-48a0-4c38-a614-2394418b8d78">

<img width="397" alt="Screenshot 2024-11-12 at 12 21 54 PM" src="https://github.com/user-attachments/assets/0a694894-0222-41c8-a043-80c48f3b9f69">


<img width="396" alt="Screenshot 2024-11-12 at 12 22 13 PM" src="https://github.com/user-attachments/assets/eb109ec5-4b47-4d9f-8c37-28c6d1213f03">

<b>&#9317;Configuring the Client VM to Use the Domain Controller's Private IP Address as Its DNS Server</b>

We will now configure the client VM (the second VM) to use the domain controller's (DC-1's) private IP address as its DNS server. This is essential for the client VM to locate and join the domain controlled by DC-1.

1. Retrieve the Domain Controller's Private IP Address:

- Navigate to DC-1 in Azure:
  
- Go to the Azure portal and select your domain controller VM (DC-1).

- Find the Private IP Address:
  
- In the Overview section or under Networking, locate the Private IP address.

- Note down this IP address; you will need it for the next steps.
  
2. Access the Client VM's Network Interface Settings:

- Navigate to Client-1 in Azure:
  
- In the Azure portal, select your client VM (Client-1).
  
- Go to Networking Settings:
  
- In the left-hand menu, click on Networking under Settings.
  
- Access the Network Interface:
  
- Under the Network interface section, click on the name of the network interface associated with Client to open its settings.
  
3. Configure DNS Server Settings:

- Select DNS Servers:
  
- In the network interface settings, select DNS servers from the left-hand menu.
  
- Change DNS Server Configuration:

- You will see that the DNS server is set to "Inherit from virtual network" by default.
  
- Change this setting to "Custom".
  
- Enter the Domain Controller's IP Address:
  
- In the DNS server field that appears, enter the private IP address of DC-1 that you noted earlier.
  
- This tells the client VM to use the domain controller as its DNS server.
  
4. Save the Changes:

- Apply the Configuration:
- Click on Save to apply the new DNS server settings to the client VM's network interface.
  
5. Restart the Client VM (Optional but Recommended):

- Ensure Settings Take Effect:
  
- To make sure the new DNS settings are applied, you may need to restart the Client-1 VM.

- In the Azure portal, select the client VM, click on Restart, and confirm when prompted.

<img width="792" alt="Screenshot 2024-11-12 at 12 42 23 PM" src="https://github.com/user-attachments/assets/7407e83d-43e4-40c1-b06b-c6d23d61223e">

<img width="791" alt="Screenshot 2024-11-12 at 12 48 02 PM" src="https://github.com/user-attachments/assets/9fe1570a-97b9-4875-950f-f6b69f4143a5">
<img width="797" alt="Screenshot 2024-11-12 at 12 48 22 PM" src="https://github.com/user-attachments/assets/23fbd97a-334e-40c9-8e49-dd38c769c6b6">

<img width="788" alt="Screenshot 2024-11-12 at 12 48 45 PM" src="https://github.com/user-attachments/assets/0f350b38-7190-4b94-b452-785bca48612f">

<img width="334" alt="Screenshot 2024-11-12 at 12 49 06 PM" src="https://github.com/user-attachments/assets/fc835d24-7763-43b5-bec6-f966a4888823">

<img width="957" alt="Screenshot 2024-11-12 at 1 28 45 PM" src="https://github.com/user-attachments/assets/68498027-ca0c-4be7-8255-3e7b471abc9a">

<b>&#9318;Verifying Connectivity Between Client-1 and the Domain Controller (DC-1)</b>

Now that the domain controller (DC-1) has restarted, we will log into Client-1 and verify connectivity by pinging the domain controller's private IP address. We will also confirm that the DNS settings on Client-1 are correctly configured to use DC-1's private IP address.

1. Obtain Client-1's Public IP Address:

- Navigate to Client-1 in Azure:
  
- In the Azure portal, go to Virtual Machines and select Client-1.
  
- Copy the Public IP Address:

- In the Overview section, locate the Public IP address.
  
- Copy this IP address for use in the RDP connection.
  
2. Log into Client-1 via Remote Desktop Protocol (RDP):

- Open RDP Client:
  
- On your local machine, open the Remote Desktop Connection application.
  
- Connect to Client-1:
  
- Enter Client-1's public IP address in the Computer field.
  
- Click Connect.
  
- Authenticate:
  
- Enter the username and password you created when setting up Client-1.
  
- Click OK to log in.
  
3. Ping the Domain Controller's Private IP Address from Client-1:

- Obtain DC-1's Private IP Address:
  
- In the Azure portal, select DC-1 (your domain controller VM).
  
- In the Overview or Networking section, locate and copy the Private IP address.
  
- Open PowerShell on Client-1:
  
- Click on the Start button (bottom-left corner) and type PowerShell.
  
- Open Windows PowerShell.
  
- Ping DC-1:
  
- In PowerShell, type the following command and press Enter:
  
- ping [DC-1's private IP address]
  
- Replace [DC-1's private IP address] with the actual IP (e.g., ping 10.0.0.4).
  
4. Verify Ping Results:
  
- Ensure that you receive 4 reply messages indicating successful communication.
  
- Successful Ping Example:

<img width="858" alt="Screenshot 2024-11-12 at 1 47 12 PM" src="https://github.com/user-attachments/assets/0a019ee3-d58b-4c8e-9ce9-7faee128d8a1">
<br/>
5. Troubleshooting:
  
- If you do not receive replies (e.g., "Request timed out"):
  
- Check Network Configuration:
  
- Ensure both VMs are in the same Virtual Network (VNet) and appropriate subnets.
  
- Firewall Settings:
  
- Confirm that the Windows Firewall on DC-1 is disabled or allows ICMP (ping) requests.
  
- Refer back to the steps where the firewall was configured on DC-1.
  
6. Verify DNS Settings on Client-1:

- In PowerShell on Client-1:
  
- Type the following command and press Enter:
  
- ipconfig /all
  
- Review DNS Server Configuration:
  
- Look for the DNS Servers entry under the network adapter in use.
  
- Confirm DNS IP address:
<img width="857" alt="Screenshot 2024-11-12 at 1 59 23 PM" src="https://github.com/user-attachments/assets/66f659d5-62d1-4b5a-89c0-dd889982640a">
<br/>

7. Troubleshooting DNS Settings:
  
- If the DNS server IP does not match DC-1's private IP:
  
- Revisit the network interface settings for Client-1 in Azure.
  
- Ensure that the DNS server is set to Custom and the IP address is set to DC-1's private IP.
  
- Save any changes and restart Client-1 to apply the new settings.

**Summary of Network Configuration and Traffic Observation**

In this exercise, we set up a virtual network in Microsoft Azure with a Windows Server acting as a domain controller and a Windows 10 client machine. We configured static IP addresses and DNS settings to enable seamless domain integration. Using Wireshark, we observed network protocols such as SSH, RDP, DHCP, DNS, and ICMP to gain insights into their behaviors. Additionally, we adjusted firewall settings to control network traffic, enhancing our understanding of network configuration, domain management, and traffic analysis within a virtualized environment.



</p>
<br />
