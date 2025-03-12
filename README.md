<h1>Observing Network Traffic in Azure Virtual Machines</h1>

![]()

<h2>Description</h2>
This project explores network traffic monitoring, firewall configurations, and security group management using Azure Virtual Machines. By leveraging tools like Wireshark, users will analyze ICMP, SSH, DNS, DHCP, and RDP traffic while configuring Network Security Groups to control access.
<br />

<h2>Overview:</h2>

- <b>Create our Virtual Machines</b> 
- <b>Observe ICMP Traffic</b>
- <b>Configuring a Firewall [Network Security Group]</b>
- <b>Observe SSH Traffic</b>
- <b>Observe DHCP Traffic</b>
- <b>Observe DNS Traffic</b> 
- <b>Observe RDP Traffic</b>

<h2>Techonologies Used</h2>

- <b>Azure</b> 
- <b>Remote Desktop</b>
- <b>Command line tools</b>
- <b>Network Protocols (SSH, DHCP, DNS, RDP)</b>
- <b>Wireshark</b>
- <b>Powershell</b>

<h2>Operating Systems</h2>

- <b>Windows 10 </b> 
- <b>Ubuntu Server</b>

<h2>Program walk-through:</h2>

<h3>Create our Virtual Machines</h3>

Create a Resource Group <br/>
 
![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.1.PNG)
<br />

Create a Windows 10 Virtual Machine (VM) <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.2a.PNG)
![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.2b.PNG)
<br />

Create a Linux (Ubuntu) VM <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.3a.PNG)
<br />

Authentication type: Username/Password <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.3b.PNG)
<br />

While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.  <br/>
Ensure both VMs are in the same Virtual Network / Subnet <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/1.4.PNG)
<br />

<h2>Observe ICMP Traffic</h2>

Use Remote Desktop to connect to your Windows 10 Virtual Machine <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.7a.PNG)
![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.7b.PNG)
<br />

Within your Windows 10 Virtual Machine, Install Wireshark <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.8.PNG)
<br />

Click on Ethernet<br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.9.PNG)
<br/>

Open Wireshark and start packet capture <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.9a.PNG)
<br />

Within Wireshark, filter for ICMP traffic only <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.10.PNG)
<br />

Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.11.PNG)
<br />

Observe ping requests and replies within WireShark  <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/2.11a.PNG)
<br />

From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark  <br/>

<h2>Configuring a Firewall [Network Security Group]</h2>

Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM <br/>
Add -t to the ping command <br/>
ping 10.0.0.5 -t <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13.PNG)
<br />

Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13a.PNG)
<br/>

Enter * for source port ranges and destination port ranges indicating any ports <br/>
Select ICMP protocol <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13a1.PNG)
<br/>

Notice our security rule denying any source and destination port <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13a2.PNG)
<br />

Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity <br/>
Notice the requests are timing out<br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13b.PNG)
<br />

Re-enable ICMP traffic for the Network Security Group by deleting the security rule<br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13c.PNG)
<br />

Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working) <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13d.PNG)
<br />

Stop the ping activity - Control C <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.13e.PNG)
<br />

<h2>Observe SSH Traffic</h2>

In Wireshark, start a packet capture up <br/>
Filter for SSH traffic only <br/>
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address) <br/>
Open PowerShell, and type: ssh labuser@10.0.0.5 <br/>
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.15.16.17.18.PNG)
<br/>

Notice labuser@linux-vm indicating we are logged in via SSH on the Linux VM  <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.18a.PNG)

Exit the SSH connection by typing ‘exit’ and pressing [Enter] <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.18b.PNG)
<br />

<h2>Observe DHCP Traffic</h2>

In Wireshark, filter for DHCP traffic only  <br/>
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line <br/>
Open PowerShell as admin and run: ipconfig /renew <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.19.20a.PNG)
<br />

Observe the DHCP traffic appearing in WireShark  <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.20b.PNG)
<br />

<h2>Observe DNS Traffic</h2>

In Wireshark, filter for DNS traffic only <br/>
From your Windows 10 VM within a command line, use nslookup to see what google.com IP addresses are <br/>
Observe the DNS traffic being show in WireShark <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.21.22.PNG)
![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.22.1.PNG)
<br />

We can use the google.com IP address (pictured above) in the browser to visit google.com

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.22.2.PNG)
<br />

<h2>Observe RDP Traffic</h2>

In Wireshark, filter for RDP traffic only (tcp.port == 3389)  <br/>
Observe the immediate non-stop spam of traffic <br/>
The RDP (protocol) is constantly showing you a live stream from one computer to another because traffic is always being transmitted  <br/>

![](https://github.com/rbrianshutt/network_activities_azure_vm/blob/main/Networking/3.23.24.PNG)
<br />






