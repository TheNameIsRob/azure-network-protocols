<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create resources in Azure
- Download the Network Protocol Analyzer WireShark
- Observe ICMP traffic
- Observe DHCP traffic
- Observe DNS traffic
- Observe DHCP traffic

<h2>Actions and Observations</h2>

Step 1: Create a Resource Group in Azure
   - Enter 'Resource Groups' in the search bar at the top
   - Click '+Create'
   - Enter your Resource Group  name, and select whichever Region that works for you
   - Click 'Review + Create' -> then click 'Create'
     
     <img src= "https://i.imgur.com/fuhZugT.png">

Step 2: Create 2 virtual machines in Azure (Windows10 and Ubuntu Linux)
- Select our resource group
- Name the Virtual Machine (VM1)
- Select a functional region
- For availability options click "No infrastructure redundancy required"
- Select CPU size of 2
- Make security type "Standard"
- Choose Windows 10 Pro for our image type
- Create an administrator account
- Select RDP protocol for our inbound port rules
- Go to the networking section and create a vnet
- Click "review+create" and wait for the Windows virtual machine to deploy.
  
<img src="https://i.imgur.com/AGPRnP8.png">

<img src="https://i.imgur.com/GgwWDzZ.png">

<img src="https://i.imgur.com/D2IzUca.png">

<img src="https://i.imgur.com/9YJhBr7.png">

<img src="https://i.imgur.com/Yg5vHQx.png">

<h3>Note: Same steps will apply for setting up our Linux virtual machine. But we will select our image type as "Ubuntu Server 24.04 LTS". We also need to select SSH as our inbound port rules to allow VM1 to access VM2 later on. Lastly, we need to make sure we use our created vnet for proper connection between both. </h3>

<img src="https://i.imgur.com/iEotZXw.png">

<img src="https://i.imgur.com/Ip5KCjk.png">

<img src="https://i.imgur.com/S7TbMJu.png">



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
