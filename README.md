<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

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

- Step 1: Create both Virtual Machines (VM) 
- Step 2: Ping one VM from the other
- Step 3: Block traffic using Network Security Groups (NSG)
- Step 4: Observe Dynamic Host Configuration Protocol (DHCP)
- Step 5: Observe RDP traffic on WireShark

<h2>Actions and Observations</h2>

<p>
  
![image](https://github.com/noahclaxton227/azure-network-protocols/assets/150629711/ebc3c72f-eee5-41a2-ae49-a57f8d1802c2)

</p>
Two virtual machines were created on Azure. One machine running Azure and the other running Linux. These were created in order to observe how these two interact with each other through the programs of Powershell and Wireshark. 
<p>
</p>
<br />

<p>
  
![image](https://github.com/noahclaxton227/azure-network-protocols/assets/150629711/04a59941-1f95-43d9-b8a8-8400cf6c954d)

</p>
<p>
Using Powershell on VM1's machine, the private IP address of VM2 (10.0.0.5) is pinged to test the reachibility of the machine.
</p>
<br />

<p>
  
![image](https://github.com/noahclaxton227/azure-network-protocols/assets/150629711/2fe3a1b2-7853-4e2d-87de-6f7c41e4449c)

</p>
<p>
Azure on our computer's original operating system can filter which protocols can go through to machine 1 or 2. Just search Azure --> open network security groups --> add a new protocol --> deny ICMP. This will deny all Ping requests on that specific machine, as Ping uses the Internet Control Message Protocol. 
</p>
<br />

<p>
  
![image](https://github.com/noahclaxton227/azure-network-protocols/assets/150629711/df3b6f00-a205-4d3a-8c8b-5992954e17fa)

</p>
<p>
The protocol DHCP (the protocol that automatically assigns IP addresses), can be used by typing the command ipconfig /renew into Powershell to renew or recieve a new IP address for that machine.
</p>
<br />

<p>
  
![image](https://github.com/noahclaxton227/azure-network-protocols/assets/150629711/8d6b9fc9-36ad-4991-af79-6838f6b91225)


</p>
<p>
Powershell can also be utilized to read the RDP activity on the device. Just type tcp.port == 3389 into Wireshark to filter RDP protocols, and because RDP is curently in use through the VM, a vast amount of lines can be read.
</p>
<br />
