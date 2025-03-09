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

<h2>Create our Virtual Machines</h2>
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
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

![]()
<br />
<br />
Lorem ipsum  <br/>

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
