<h1>Setting up DNS and Routing</h1>

<h2>Description</h2>
This is a simple set up using a hypervisor to set DNS and Routing on a Windows Server
<br />


<h2>Languages and Utilities Used</h2>

- <b>VirtualBox</b> 

<h2>Environments Used </h2>

- <b>Windows Server 2019</b>

<h2>Set Up Walk-through:</h2>

<p align="center">
In the server manager select add roles and features. Click next until you get to server selection select there should only be one server on the list select it and click next: <br/>
<img src="https://i.imgur.com/lPeS9Eh.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Under select server roles, select active directory domain services. Click next through to the install button:  <br/>
<img src="https://i.imgur.com/gga2Cd0.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
In the top right there will be a yellow trouble flag in notifications. Click it then select promote the server to a domain contoller: <br/>
<img src="https://i.imgur.com/48LxTPq.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Check add new forest and name it whatever you want then click next. Create a password you'll remember then click next. As the following screens auto populate, click next until you reach the install screen then click install. The VM will restart:  <br/>
<img src="https://i.imgur.com/5preGAS.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Next you'll set up a remote access server for network address translation. This is going to allow the clients on the virtual private network to accesss the internet through this server. In the server manager select add roles and features then click next until you get to server selection select. There should only be one server on the list, select it and click next:  <br/>
<img src="https://i.imgur.com/uo0teTv.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Under select server roles select remote access. Click next:  <br/>
<img src="https://i.imgur.com/JpX6FWa.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Then under role services select routing. Click next through to install:  <br/>
<img src="https://i.imgur.com/pgmZAoi.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
When the install is complete, click the tools drop down in the top right corner and select routing and remote access:  <br/>
<img src="https://i.imgur.com/eV9ePrm.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Right click your device's name and select configure and enable routing and remote access:  <br/>
<img src="https://i.imgur.com/2E9HOJm.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Check Network Address Translation (NAT) then click next:  <br/>
<img src="https://i.imgur.com/26cBqG2.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Select *use the public interface to connect to the internet. Select the network adapter with the internet connection. *if its greyed out, close the dialog box and start again from selecting routing and remote access from the tools menu. Click next then finish:  <br/>
<img src="https://i.imgur.com/WOA2A43.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Next you'll set up a DHCP which will all allow other windows clients to get and IP address from the Domain Controller. This will allow those clients to connect to and browse the internet. In the server manager select add roles and features again then Select DHCP under Server Roles then click next through to install. When it completes, from the tools dropdown, select DHCP:  <br/>
<img src="https://i.imgur.com/YiGJI5J.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Click the arrow next to your server:  <br/>
<img src="https://i.imgur.com/TfqUYWy.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Right click the IPv4 and select New Scope:  <br/>
<img src="https://i.imgur.com/VBrS4Gb.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Name the scope what ever you want:  <br/>
<img src="https://i.imgur.com/PRpc7bj.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Set you desired IP range and your subnet mask. In this lab I set Start IP to 172.16.0.100 End IP to 172.16.0.200 with a length to 24, which will be a Mask of 255.255.255.0 in CIDR notation. You don't need to add exclusions, but you can if  you wanted to manually set the IP address for certain devices:  <br/>
<img src="https://i.imgur.com/Fs0qpP5.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Lease duration in this lab you can set the days as high as you want. This sets how long your device will have a certain IP before it needs to be renewed through the DHCP server:  <br/>
<img src="https://i.imgur.com/nmVZUrh.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
The DC will serve as the router(default gateway) so use the DC IP address 172.16.0.1 and click Add then Next all the way through to finish:  <br/>
<img src="https://i.imgur.com/0tgE8Ml.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
<br />
<br />
Once complete right click your server and select Authorize. With that the server is ready to go. Workstation computer connected to this server will be assigned an IP and be able to access the internet:  <br/>
<img src="https://i.imgur.com/Bwrdqo3.png" height="80%" width="80%" alt="Setting up DNS and Routing"/>
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
