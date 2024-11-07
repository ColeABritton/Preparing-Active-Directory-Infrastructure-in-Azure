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
Create a resource group within Microsoft Azure <br/>
<img src="https://i.imgur.com/mn2KoJx.png" height="80%" width="80%" alt="Create Resource Group"/>
<br />
<br />
Create a virtual network making sure to put it in the resource group we just created. Allow a few minutes for the v-net to deploy before continuing to the next step. <br/>
<img src="https://i.imgur.com/7QM3Een.png" height="80%" width="80%" alt="Create Virtual Network"/>
<br />
<br />
Create the first virtual machine that will act as our Domain Controller and host for Active Directory, making sure to select Windows Server 2022 as the image. <br/>
<img src="https://i.imgur.com/S9Fgu7q.png" height="80%" width="80%" alt="Create Domain Controller"/>
<img src="https://i.imgur.com/ujaGLIE.png" height="80%" width="80%" alt="Domain Controller Login Credentials"/>
<br />
<br />
Navigate to the Networking section and select the Virtual Network we previously created, ensuring it deploys within the same network as our Client VM created in the next step. Leave the remaining settings as is then Review + Create. <br/>
<img src="https://i.imgur.com/g4wQOlj.png" height="80%" width="80%" alt="Domain Controller Deploy Within Created Virtual Network"/>
<br />
<br />
Create the second virtual machine that will act as our Client, making sure to select Windows 10 as the image, and confirming the Licensing before continuing to the next step. <br/>
<img src="https://i.imgur.com/CcaWXnv.png" height="80%" width="80%" alt="Client Creation"/>
<img src="https://i.imgur.com/6ExHYiu.png" height="80%" width="80%" alt="Client Login Credentials"/>
<br />
<br />
Navigate to the networking section and select the Virtual Network we previously created once again. Leave the remaining settings as is then Review + Create. <br/>
<img src="https://i.imgur.com/kYjKSu1.png" height="80%" width="80%" alt="Client Deploy Within Created Virtual Network"/>
<br />
<br />
Open the Domain Controller VM within Azure navigate to Networking -> Network Settings then click on the Network interface. Now, we will go to Settings -> IP configurations -> ipconfig1 then change the Private IP address allocation from Dynamic to Static then Save. Doing this will ensure our Domain Controller VM can double as our DNS server, which our Client VM will use later. <br/>
<img src="https://i.imgur.com/hVLdrCI.png" height="80%" width="80%" alt="Domain Controller Network Interface Controller"/>
<img src="https://i.imgur.com/3FUVOUi.png" height="80%" width="80%" alt="Domain Controller Static IP"/>
<br />
<br />
Now, copy and paste the Domain Controller Public IP Address into Remote Desktop Connection then Connect, and login with the VM credentials. You should be greeted by the Server Manager. <br/>
<img src="https://i.imgur.com/6L3xdhA.png" height="80%" width="80%" alt="Remote Desktop into Domain Controller"/>
<img src="https://i.imgur.com/tJSnkfK.png" height="80%" width="80%" alt="Domain Controller First Login"/>
<br />
<br />
Right-click the Start button (Windows Logo), select Run then type wf.msc to open the Firewall Settings. Next, open the Windows Defender Firwall Properties then turn the Firewall state to Off on all three profiles and Apply. This isn't something we would do in a real-world IT setting, but for learning purposes we will do it. We can now close the Remote Desktop Connection as we are done configuring things on the DC. <br/>
<img src="https://i.imgur.com/lXnRiJ1.png" height="80%" width="80%" alt="Windows Run Firewall"/>
<img src="https://i.imgur.com/iWhjlkT.png" height="80%" width="80%" alt="Turn Firewall Off"/>
<br />
<br />
Navigate to the DomainController VM within Azure and copy the Private IP address under Networking. <br/>
<img src="https://i.imgur.com/IxkrFYq.png" height="80%" width="80%" alt="Domain Controller Private IP"/>
<br />
<br />
Navigate to the Client VM within Azure and access the Network Interface. Now go to Settings -> DNS servers -> Paste the DC's private IP and Save. Make sure to restart the Client VM to process these changes before continuing. <br/>
<img src="https://i.imgur.com/WeLPEQD.png" height="80%" width="80%" alt="Client Network Interface Controller"/>
<img src="https://i.imgur.com/rU3u61s.png" height="80%" width="80%" alt="Edit Client DNS"/>
<br />
<br />
Now, copy and paste the Client VM Public IP Address into Remote Desktop Connection then Connect, and login with the VM credentials. <br/>
<img src="https://i.imgur.com/QPHk53s.png" height="80%" width="80%" alt="Remote Desktop into Client"/>
<br />
<br />
Search for Windows PowerShell and open as an administrator. We will attempt to ping the Domain Controller using the ping command followed by the private IP address. You should recieve some replies from the DC. <br/>
<img src="https://i.imgur.com/2Tt2CVJ.png" height="80%" width="80%" alt="Client Ping DNS IP"/>
<br />
<br />
Now, we will run the command 'ipconfig /all' to ensure we properly connected the Client to the DNS Server. <br/>
<img src="https://i.imgur.com/SjQBjPS.png" height="80%" width="80%" alt="IPconfig /all DNS Server IP"/>
<br />
<br />
<h2>Active Directory Infrastructure is Fully Setup! </h2>
