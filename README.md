<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />






<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (ICMP, SSH, DHCP, DNS, RDP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create resources in Azure
- Download the Network Protocol Analyzer WireShark
- Observe ICMP traffic
- Observe DHCP traffic
- Observe SSH Traffic
- Observe DNS traffic
- Observe RDP traffic

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
- Click "review+create" and wait for the virtual machine to deploy.
- Observe that both have been created
  
<img src="https://i.imgur.com/AGPRnP8.png">

<img src="https://i.imgur.com/GgwWDzZ.png">

<img src="https://i.imgur.com/D2IzUca.png">

<img src="https://i.imgur.com/9YJhBr7.png">

<img src="https://i.imgur.com/Yg5vHQx.png">

<h3>Note: Same steps will apply for setting up our Linux virtual machine. But we will select our image type as "Ubuntu Server 24.04 LTS". We also need to select SSH as our inbound port rules to allow VM1 to access VM2 later on. Lastly, we need to make sure we use our created vnet for proper connection between both. </h3>

<img src="https://i.imgur.com/iEotZXw.png">

<img src="https://i.imgur.com/Ip5KCjk.png">

<img src="https://i.imgur.com/S7TbMJu.png">

<img src="https://i.imgur.com/3YmKS32.png">

Step 3: Log into the Windows 10 virtual machine using Remote Desktop Connection on your current computer.
- Specify the computer you will be using by typing in your public IP address and your administrator username. Shortly after type your password.
- As soon as windows 10 is open up Internet explorer and download WireShark Protocol analyzer.
- Download Windows installer
- Search for Wireshark in the search menu and open.
- Click ethernet and the blue fin on the top left to start observing active network traffic.

<img src="https://i.imgur.com/tKlpn78.png">

<img src="https://i.imgur.com/Ug38MJS.png">

<img src="https://i.imgur.com/sOeXufd.png">

<img src="https://i.imgur.com/kXnKqua.png">

<img src="https://i.imgur.com/LJsD1Nc.png">

<img src="https://i.imgur.com/IDtLwm9.png">

<img src="https://i.imgur.com/67L4rmG.png">

<img src="https://i.imgur.com/cf8gjpp.png">

Step 3: Start observing different kinds of network traffic.

<h3>ICMP traffic </h3>

   - Filter for ICMP in WireShark
     
   - Test connectivity between Windows 10 and Ubuntu Linux by pinging the private IP address. ("ping 10.0.0.5)
   
   - Create a nonstop ping using the command "ping -t"
   
   - Go into inbound security rules in Azure for our Linux virtual machine (VM2) and configure the firewall to disable ICMP traffic from reaching Windows 10.
     
   - Enable the firewall and allow traffic again and observe the change.
     
<img src="https://i.imgur.com/qY3QmB7.png">

<img src="https://i.imgur.com/XYwls64.png">

<img src="https://i.imgur.com/ZmM5l5i.png">

<img src="https://i.imgur.com/jbedNxJ.png">

<img src="https://i.imgur.com/R6DPE0u.png">

We are using VM1 to test its reachability to VM2 by using ICMP (Internet Control Message Protocol), which allows us to receive data based on the connectivity between both machines. By using the `ping` command in PowerShell, we can send an ICMP Echo Request to VM2. We can then observe the response in Wireshark to determine if the connection between both machines was successful.

<h3>SSH Traffic</h3>

- Filter for SSH in WireShark

- Use the command "ssh labuser1@10.0.0.5" to access the Linux command line remotely by using the credentials to log in.

- Type commands (touch and ls -la) into the linux SSH connection and observe SSH traffic spam in WireShark
  
- Exit the SSH connection by typing ‘exit’ and pressing

  <img src="https://i.imgur.com/CIrC4Zr.png">

  <img src="https://i.imgur.com/H1lYoy6.png">

  <img src="https://i.imgur.com/ZdTTlXR.png">

With the SSH protocol, we can securely access and managing another device from the device you're currently using. In this case VM1 is accessing VM2 and we can observe all this activity in Wireshark which will display our network traffic.

  <h3>DHCP</h3>
  - Filter for DHCP in WireShark
  
  - Type in ipconfig /renew  
  
  - Observe the DHCP traffic appearing in WireShark

   <img src="https://i.imgur.com/XigPV1G.png">

In WireShark we are simply seeing whether the process of this protocol taking place is actually functioning. DHCP allows a computer (or any network device) to automatically receive an IP address and other necessary network configuration details from a DHCP server. This automatic assignment ensures that the device can properly function within the network by having a unique IP address, which is essential for communication and access to network resources.

<h3>DNS </h3>

- Filter for DNS in Wireshark.

- Use "nslookup" to obtain your IP address and view DNS traffic in WireShark

- Additionally, use "nslookup www.google.com" to view the websites public IP address and observe WireShark

<img src="https://i.imgur.com/Kxafhga.png">

<h3>RDP Traffic</h3>

- In WireShark filter for RDP by using ""tcp.port == 3389"" in our filter search bar.
  
- Observe all the active traffic taking place

<img src="https://i.imgur.com/zsdLNMm.png">

<img src="https://i.imgur.com/rfB8QNx.png">

The RDP protocol allows us to watch all live traffic between both of our virtual machines. RDP relies on TCP port 3389 for communication which is why we specifically used "tcp.port == 3389" to filter for RDP traffic.




