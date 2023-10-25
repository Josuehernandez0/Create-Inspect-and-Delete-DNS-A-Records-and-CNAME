# Create Inspect and Delete DNS A Records and CNAME
<p align="center">
<img src=""/>
</p>

<h1>Create Inspect and Delete DNS A Records and CNAME</h1>
In this tutorial, going off On-premises Active Directory Deployed in the Cloud (Azure) [https://github.com/josuehernandez0/Configuring-On-premises-Active-Directory-within-Azure-VMs] we will Create Inspect and Delete DNS A Records and CNAME in DC-1 VM . <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop Connection
- Active Directory Domain Services
- Server Manager
- DNS Manager
- Command Prompt (Admin)


<h2>Operating Systems Used </h2>

- Windows 10 (21H2)

<h2>High-Level Steps</h2>

- Log into Cilent-1 and DC-1 VM from [https://github.com/josuehernandez0/Configuring-On-premises-Active-Directory-within-Azure-VMs]
- Go to DC-1 VM/ DNS Manager/ Forward Lookup Zones / Create A Record
- Open Cilent-1 VM ping A Record from DC-1
- Flush DNS and Display DNS on Cilent-1
- Open DC-1 VM and change the name of the A Record
- Open Cilent-1 VM Ping the new name of A Record
- Go back to DC-1 VM and create a CNAME
- Open Cilent-1 VM and Ping CNAME
- Go back to DC-1 VM and see Root Hints File


<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/josuehernandez0/Create-Inspect-and-Delete-DNS-A-Records-and-CNAME/assets/143027686/ab091d4c-4b4b-4034-9488-9f27b0d25530"/>
</p>
<p>
First we need to log back into Cilent-1 and DC-1 from [https://github.com/josuehernandez0/Configuring-On-premises-Active-Directory-within-Azure-VMs] using Remote Desktop Connection. Copy the Public IP and log into the VM indivudally.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next open Cilent-1 VM and search for Command Prompt in the search bar.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Once CMD loads you will see you are under jane_admin.
</p>
<br />


<p>
<img src=""/>
</p>
<p>
Then Open DC-1 VM and click Tools on the top right side of Server Manager. Then select DNS.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next click the DC-1 File.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Then click Forward Lookup Zones.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next double click mydomain.com folder
</p>
<br />

<p>
<img src=""/>
</p>
<p>
We are now going to create a New Host A Record. To do this right click anywhere on the screen and click New Host (A or AAAA)...
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now in the Name section we can type mainframe and for IP Address we can type the same IP as dc-1 IP which is 10.0.0.4. Once those are both typed in click add host.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Once you added the host click ok.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Then click done to finish the process.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next go back to Cilent-1 VM and ping the A Record we created. Type ping mainframe in the command line 4 packets will be sent and received from DC-1 to Cilent-1.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
We can also lookup the IP Address by typing nslookup mainframe in the command line.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next type ipconfig /displaydns in the command line this will display all the websites search on this VM.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Then we can clear the DNS cache by typing ipconfig /flushdns in the command line.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
The command line wont let use run this command, close CMD. Then when you re open Command Prompt right click and run as administrator.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Click yes to allow Windows Command Processor to run.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Go back to DC-1 VM and double click mainframe and this time change the IP Address to 8.8.8.8 and click ok on the bottom left.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now we can see that mainframe IP Address changed to 8.8.8.8
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Go back to Cilent-1 VM and type ping mainframe and it will still ping the IP Address even though we changed it.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
We can type ipconfig /displaydns to see what we pinged.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next type ipconfig /flushdns in the commandline to flush the DNS Resolver Cache.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now type ping search in the command line you wil see the ping request could not find host search. Which means its not created yet.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Go back to DC-1 VM and right click anywhere, then click New Alias (CNAME).
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now in the Alias name section type search, and under fully qualified domain name type www.google.com then you can press ok.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now we can see that search was created.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Go back to Cilent-1 VM and type ping search in the command line. 4 packets will be send and received from www.google.com
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Next type ipconfig /displaydns and we will see the ping that we just did.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Now type ipconfig /flushdns this will flush the DNS cache again.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Go back to DC-1 VM and right click DC and go to properties.
</p>
<br />

<p>
<img src=""/>
</p>
<p>
Click on the Root Hints tab and you will see all the Root Hints in DC-1
</p>
<br />
