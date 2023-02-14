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

<h2>Create our Resources</h2>

Part 1 (Create our Resources)


Create a Resource Group

Create a Windows 10 Virtual Machine (VM)

While creating the VM, select the previously created Resource Group

While creating the VM, allow it to create a new Virtual Network (Vnet) and Subnet

Create a Linux (Ubuntu) VM

While create the VM, select the previously created Resource Group and Vnet

Observe Your Virtual Network within Network Watcher


<h2>Setting Up Resources</h2>

<p>
<img src="https://i.imgur.com/4QC24A2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Once we have all of our prerequisites in place, we can Observe ICMP Traffic.
</p>
<br />

Part 2 (Observe ICMP Traffic)

Use Remote Desktop to connect to your Windows 10 Virtual Machine

Within your Windows 10 Virtual Machine, Install Wireshark

Open Wireshark and filter for ICMP traffic only

Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM

Observe ping requests and replies within WireShark

From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark

Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM

Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic

Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity

Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using

Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working)

Stop the ping activity

<p>
  
<img src="https://i.imgur.com/jbLuIDP.png" height="80%" width="80%" alt=""/>
</p>
<p>
We've set up our resources and began anaylzing the ICMP traffic from V1 To V2, next we will observe SSH traffic.
</p>
<br /> 

Part 2 (Observe SSH Traffic)

Back in Wireshark, filter for SSH traffic only

From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address)

Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark

Exit the SSH connection by typing ‘exit’ and pressing [Enter]


<p>
<img src="https://i.imgur.com/Sg0xV4o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we will observe DHCP Traffic. 
</p>
<br />

DHCP Traffic

Back in Wireshark, filter for DHCP traffic only

From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)

Observe the DHCP traffic appearing in WireShark 


<p>
<img src="https://i.imgur.com/kfDx6vY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we will observe DNS Traffic. 
</p>
<br /> 

Part 2 (Observe DNS Traffic)

Back in Wireshark, filter for DNS traffic only

From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are

Observe the DNS traffic being show in WireShark

<p>
<img src="https://i.imgur.com/HqOpqX0.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Next we will observe RDP Traffic. 
</p>
<br />  

Observe RDP Traffic


Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)

Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?

Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted 

<p>
<img src="https://i.imgur.com/N4vOgoZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Congratulations! We've succesfully observed: SSH, RDP, DNS, DHCP and ICMP traffic between V1 (Windows 10) and V2 (Linux). 
</p>
<br /> 
