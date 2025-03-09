<h1>Performing Activities on the Network</h1>

![]()

<h2>Description</h2>
Lorem ipsum
<br />

<h2>Techonologies Used</h2>

- <b>Azure</b> 
- <b>Remote Desktop</b>
- <b>Command line tools</b>
- <b>Network Protocols (SSH, DHCP, DNS, RDP)</b>
- <b>Wireshark</b>

<h2>Operating Systems</h2>

- <b>Windows 10 </b> 
- <b>Ubuntu Server</b>

<h2>Program walk-through:</h2>

<h3>Create our Virtual Machines</h3>

Create a Resource Group <br/>
 
![]()
<br />
<br />
Create a Windows 10 Virtual Machine (VM) <br/>

![]()
<br />
<br />
Create a Linux (Ubuntu) VM <br/>

![]()
<br />
<br />
While creating the VM, select the previously created Resource Group and Virtual Network—the Virtual Network MUST BE THE SAME.  <br/>

![]()
<br />
<br />
Authentication type: Username/Password <br/>

![]()
<br />
<br />
Ensure both VMs are in the same Virtual Network / Subnet <br/>

![]()
<br />
<br />
<h3>Observe ICMP Traffic</h3>

Use Remote Desktop to connect to your Windows 10 Virtual Machine <br/>

![]()
<br />
<br />

Within your Windows 10 Virtual Machine, Install Wireshark <br/>

![]()
<br />
<br />
Open Wireshark and start packet capture <br/>

![]()
<br />
<br />
Within Wireshark, filter for ICMP traffic only <br/>

![]()
<br />
<br />
Retrieve the private IP address of the Ubuntu VM (linux-vm) and attempt to ping it from within the Windows 10 VM <br/>

![]()
<br />
<br />
Observe ping requests and replies within WireShark  <br/>

![]()
<br />
<br />
From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) and observe the traffic in WireShark  <br/>

![]()
<br />
<br />
<h3>Configuring a Firewall [Network Security Group]</h3>

Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM <br/>

![]()
<br />
<br />
Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic <br/>

![]()
<br />
<br />
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity <br/>

![]()
<br />
<br />
Re-enable ICMP traffic for the Network Security Group <br/>

![]()
<br />
<br />
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working) <br/>

![]()
<br />
<br />
Stop the ping activity <br/>

![]()
<br />
<br />
<h3>Observe SSH Traffic</h3>

In Wireshark, start a packet capture up <br/>
Filter for SSH traffic only <br/>
From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address) <br/>
Open PowerShell, and type: ssh labuser@10.0.0.5 <br/>
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark <br/>
Exit the SSH connection by typing ‘exit’ and pressing [Enter] <br/>

![]()
<br />
<br />
<h3>Observe DHCP Traffic</h3>

In Wireshark, filter for DHCP traffic only  <br/>
From your Windows 10 VM, attempt to issue your VM a new IP address from the command line <br/>
Open PowerShell as admin and run: ipconfig /renew <br/>

![]()
<br />
<br />
Observe the DHCP traffic appearing in WireShark  <br/>

![]()
<br />
<br />
<h3>Observe DNS Traffic</h3>

In Wireshark, filter for DNS traffic only <br/>
From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are <br/>
Observe the DNS traffic being show in WireShark <br/>

![]()
<br />
<br />
<h3>Observe RDP Traffic</h3>

In Wireshark, filter for RDP traffic only (tcp.port == 3389)  <br/>
Observe the immediate non-stop spam of traffic <br/>
The RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted  <br/>

![]()
<br />
<br />



<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
