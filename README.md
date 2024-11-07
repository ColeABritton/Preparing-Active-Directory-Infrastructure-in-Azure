<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Preparing Active Directory Infastructure in Azure</h1>
This tutorial will focus on creating and configuring two Vitrual Machines, one acting as our Domain Controller running Windows Server, and the other acting as our Client that will join the Domain Server.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure
- Remote Desktop Connection
- Virtual Machines

<h2>Operating Systems Used </h2>

- Windows Server
- Windows 10 Pro

<h2>Virtual Machine Configuration and Deployment</h2>
<p>
Create a resource group within Microsoft Azure
<img src="https://i.imgur.com/mn2KoJx.png" height="80%" width="80%" alt="Create Resource Group"/>
<br />
<br />
Create a virtual network making sure to put it in the resource group we just created. Allow a few minutes for the v-net to deploy before continuing to the next step.
<img src="https://i.imgur.com/7QM3Een.png" height="80%" width="80%" alt="Create Virtual Network"/>
<br />
<br />
Create and setup the virtual machine that will be our Domain Controller.
<img src="https://i.imgur.com/S9Fgu7q.png" height="80%" width="80%" alt="Create Domain Controller"/>
<img src="https://i.imgur.com/ujaGLIE.png" height="80%" width="80%" alt="Domain Controller Login Credentials"/>
<br />
<br />
<img src="https://i.imgur.com/g4wQOlj.png" height="80%" width="80%" alt="Domain Controller Deploy Within Created Virtual Network"/>
<br />
<br />
<img src="https://i.imgur.com/CcaWXnv.png" height="80%" width="80%" alt="Client Creation"/>
<br />
<br />
<img src="https://i.imgur.com/6ExHYiu.png" height="80%" width="80%" alt="Client Login Credentials"/>
<br />
<br />
<img src="https://i.imgur.com/kYjKSu1.png" height="80%" width="80%" alt="Client Deploy Within Created Virtual Network"/>
<br />
<br />
<img src="https://i.imgur.com/hVLdrCI.png" height="80%" width="80%" alt="Domain Controller Network Interface Controller"/>
<br />
<br />
<img src="https://i.imgur.com/3FUVOUi.png" height="80%" width="80%" alt="Domain Controller Static IP"/>
<br />
<br />
<img src="https://i.imgur.com/6L3xdhA.png" height="80%" width="80%" alt="Remote Desktop into Domain Controller"/>
<br />
<br />
<img src="https://i.imgur.com/tJSnkfK.png" height="80%" width="80%" alt="Domain Controller First Login"/>
<br />
<br />
<img src="https://i.imgur.com/lXnRiJ1.png" height="80%" width="80%" alt="Windows Run Firewall"/>
<br />
<br />
<img src="https://i.imgur.com/iWhjlkT.png" height="80%" width="80%" alt="Turn Firewall Off"/>
<br />
<br />
<img src="https://i.imgur.com/IxkrFYq.png" height="80%" width="80%" alt="Domain Controller Private IP"/>
<br />
<br />
  <img src="https://i.imgur.com/WeLPEQD.png" height="80%" width="80%" alt="Client Network Interface Controller"/>
<br />
<br />
<img src="https://i.imgur.com/rU3u61s.png" height="80%" width="80%" alt="Edit Client DNS"/>
<br />
<br />
<img src="https://i.imgur.com/2Tt2CVJ.png" height="80%" width="80%" alt="Client Ping DNS IP"/>
<br />
<br />
<img src="https://i.imgur.com/SjQBjPS.png" height="80%" width="80%" alt="IPconfig /all DNS Server IP"/>
