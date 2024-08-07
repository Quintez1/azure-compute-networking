<p align="center">
<img src="https://i.imgur.com/4hzgUaF.jpeg" alt="Azure logo"/>
</p>

<h1>Lab - Azure Compute and Networking</h1>
This lab focuses on creating and managing Azure virtual machines (VMs) and understanding network traffic using tools like Wireshark. You'll create both Windows and Linux VMs, observe different types of network traffic (ICMP, SSH, DHCP, DNS, and RDP), and understand how network security groups (NSGs) can affect this traffic. This lab will help you build fundamental skills in Azure computing and networking, and how to analyze and secure network traffic.<br />

<h2>Environments and Technologies Used</h2>

- Azure Portal
- Windows 10 VM
- Ubuntu Linux VM
- Wireshark
- Network Security Groups (NSGs)
- Remote Desktop Protocol (RDP)

<h2>Operating Systems Used </h2>

- Windows 10</b> (21H2)

<h2>Installation Steps</h2>

Part 1: Create Resources
- Create a Resource Group:

Navigate to the Azure Portal.
Select "Resource groups" from the left-hand menu.
Click "Add".
Enter a name for the Resource Group (e.g., Lab2ResourceGroup).
Select a region close to you or based on your needs.
Click "Review + create" and then "Create".
<img src="https://i.imgur.com/x7ihWC0.png" alt="Create Resource Group"/>

- Create a Windows 10 Virtual Machine (VM):

Select "Virtual machines" from the left-hand menu in the Azure Portal and click "Add".
Choose the Resource Group you created earlier.
Enter a name for the VM (e.g., Windows10VM).
Select "Windows 10 Pro" as the image.
Choose a size that fits your requirements (e.g., Standard D2s_v3).
Set up the Administrator account with a username and password.
In the "Networking" tab, ensure a new Virtual Network (Vnet) is created.
Click "Review + create" and then "Create".
<img src="https://i.imgur.com/GsM6UrL.png" alt="Create Windows 10 Virtual Machine"/>
<img src="https://i.imgur.com/dlGAp9K.png" alt="Create Windows 10 Virtual Machine"/>

- Create a Linux (Ubuntu) VM:

Go to "Virtual machines" in the Azure Portal and click "Add".
Select the same Resource Group created previously.
Enter a name for the VM (e.g., UbuntuVM).
Choose "Ubuntu Server 20.04 LTS" as the image.
Select a VM size (e.g., Standard B1ms).
Set up the authentication type (e.g., SSH public key) and provide the necessary details.
Ensure it uses the same Virtual Network (Vnet) created earlier.
Click "Review + create" and then "Create".
<img src="https://i.imgur.com/1J7HB2E.png" alt="Create a Linux (Ubuntu) VM"/>

- Part 2: Remote Desktop

- Connect to the Windows 10 VM using Remote Desktop:

Open Remote Desktop Connection on your local machine.
Enter the public IP address of the Windows 10 VM.
Log in using the Administrator account credentials you set up.
<img src="https://i.imgur.com/WvycDdu.png" alt="Connect to Remote Desktop"/>
<img src="https://i.imgur.com/Bfk58cF.png" alt="Login (Remote Desktop"/>

- Install Wireshark:

Open a web browser in the Windows 10 VM.
Download and install Wireshark from Wireshark’s official website.
Open Wireshark and set the filter to ICMP to capture ICMP traffic only.
<img src="https://i.imgur.com/ydHcWAo.png" alt="Wireshark Install"/>

- Ping Ubuntu VM from Windows 10 VM:

Retrieve the private IP address of the Ubuntu VM from the Azure Portal.
Open Command Prompt in the Windows 10 VM.
Run the command ping <UbuntuVM-private-IP> and observe the traffic in Wireshark.
<img src="https://i.imgur.com/GYdvMOX.png" alt="Ping Ubuntu VM from Windows 10 VM"/>
<img src="https://i.imgur.com/NUoS3nQ.png" alt="Run Ping Command"/>

- Disable/Enable ICMP Traffic:

Navigate to the Network Security Group (NSG) associated with the Ubuntu VM in the Azure Portal.
In the "Inbound security rules", disable the rule that allows ICMP traffic.
Observe the changes in Wireshark on the Windows 10 VM.
Re-enable the ICMP traffic rule and observe the traffic again.

- Part 3: Observe SSH Traffic
Filter for SSH traffic in Wireshark:
In Wireshark, change the filter to ssh.
Use an SSH client (e.g., PuTTY) on the Windows 10 VM to connect to the Ubuntu VM using its private IP address.
Log in and execute some commands in the SSH session.
Observe the SSH traffic in Wireshark.
<img src="https://i.imgur.com/nRvRTMP.png" alt="SSH Traffic"/>


- Part 4: Observe DHCP Traffic
Filter for DHCP traffic in Wireshark:
In Wireshark, change the filter to DHCP.
Open Command Prompt in the Windows 10 VM and run ipconfig /renew to request a new IP address.
Observe the DHCP traffic in Wireshark.

- Part 5: Observe DNS Traffic
Filter for DNS traffic in Wireshark:
In Wireshark, change the filter to DNS.
Open Command Prompt in the Windows 10 VM and use nslookup to find the IP addresses of google.com and disney.com.
Observe the DNS traffic in Wireshark.

- Part 6: Observe RDP Traffic
Filter for RDP traffic in Wireshark:
In Wireshark, change the filter to tcp.port == 3389.
Observe the continuous RDP traffic and understand why it’s always transmitting data.

- Lab Cleanup
Delete Resource Groups:
Close all Remote Desktop connections.
Navigate to "Resource groups" in the Azure Portal.
Select the Resource Group created for this lab and click "Delete Resource Group".
Confirm the deletion and ensure all resources are removed.
</p>
<br />
