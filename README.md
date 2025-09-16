<p align="center">
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/08b4eda2-473f-4cc3-a35e-44f13257e740" />


</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (24H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1818" height="721" alt="image" src="https://github.com/user-attachments/assets/d67a6fc9-69d1-45ca-b4de-0f686505a617" />

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="963" height="537" alt="image" src="https://github.com/user-attachments/assets/a77c5d8d-88f6-4b57-bccf-1ebfa9abed2c" />

</p>
<p>
After information was inputted, I pressed review/create.
</p>
<br />

<p>
<img width="982" height="795" alt="image" src="https://github.com/user-attachments/assets/3912b30e-5e47-4414-a53c-7e0448e31220" />


</p>
<p>
I looked up "Virtual Network" in the Azure search bar, and clicked the create button. The Vnet would be create by itself when I create the virtual machine, but I decided to make it on my own first (change this). Also clicked review+create.
</p>
<br />

<p>
<img width="1445" height="790" alt="image" src="https://github.com/user-attachments/assets/27af529d-d3c9-4344-bd83-79a3681e3a9c" />

</p>
<p>
I searched for Virtual Machine then clicked create, choosing the first option for a basic virtual machine. This VM is for the domain controller.
</p>
<br />

<p>
<img width="981" height="758" alt="image" src="https://github.com/user-attachments/assets/e43ebe78-982b-42e5-80df-bbd595677b27" />

</p>
<p>
I also set a username and password for the VM.
</p>
<br />

<p>
<img width="997" height="795" alt="image" src="https://github.com/user-attachments/assets/140a432c-b2d6-4049-bc98-8ee6de0631da" />

</p>
<p>
Also clicked review+create
</p>
<br />

<p>
<img width="1056" height="788" alt="image" src="https://github.com/user-attachments/assets/4af22b56-fb36-46d5-b614-377a807bb47b" />

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="970" height="786" alt="image" src="https://github.com/user-attachments/assets/2b1e7304-ff0b-4f5b-8bf3-a4031cd48bf6" />

</p>
<p>
Also set username and password. I put this VM in the Active-Directory-Vnet aswell. Everything else is the same as dc-1 VM. Clicked review+create.
</p>
<br />

<p>
<img width="1441" height="685" alt="image" src="https://github.com/user-attachments/assets/06a3651e-b145-4532-b73e-ac3b99b90db8" />

</p>
<p>
Private IP-address for dc-1 needs to be static so I can manually configure the settings of client-1 to use dc-1 as it's dns server. I clicked the dc-1 VM and went to the Network Settings tab. Once there, I clicked the link to edit the Network Interface Card (NIC).
</p>
<br />

<p>
<img width="1893" height="731" alt="image" src="https://github.com/user-attachments/assets/6ceaac17-4fa8-43bd-8f95-2cae24c8052a" />

</p>
<p>
I clicked the link for "ipconfig1" which opened the edit tab. I changed the private IP address allocation from dynamic to static then clicked save.
</p>
<br />

<p>
<img width="1077" height="145" alt="image" src="https://github.com/user-attachments/assets/c0ff6537-a939-45f3-a872-9cc12e4380c6" />

</p>
<p>
The Private IP address is now listed as static.
</p>
<br />

<p>
<img width="1838" height="555" alt="image" src="https://github.com/user-attachments/assets/5b273339-82c3-4e00-a0e1-6e3a5f3699ff" />

</p>
<p>
Next I went to log into the dc-1 VM using remote desktop. I entered the public IP address into the Windows remote connection, then logged in with the username and password I created.
</p>
<br />

<p>
<img width="517" height="261" alt="image" src="https://github.com/user-attachments/assets/5398e708-7f7d-4ebf-8925-d9e1b503ac57" />

</p>
<p>
Server Manager imediately opens upon logging in. I needed to disable the Windows firewall settings (not smart in real life, just for the sake of this project). I opened "Run" from the start menu and typed wf.msc. 
</p>
<br />

<p>
<img width="1303" height="925" alt="image" src="https://github.com/user-attachments/assets/94debaad-8b9b-4be8-83f3-5ec4f4e4cfb8" />

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1301" height="912" alt="image" src="https://github.com/user-attachments/assets/cf70b3ff-f6d1-485a-9075-bd75ae282ead" />

</p>
<p>
I clicked properties and clicked off for the firewall state for the domain, public, and private profiles. Clicked apply then OK.
</p>
<br />

<p>
<img width="1617" height="731" alt="image" src="https://github.com/user-attachments/assets/816cf33e-b9e4-4539-a0ea-9ee638b6b6ec" />

</p>
<p>
I acquired dc-1's private IP address from Azure. I then went to the network settings of client-1 and clicked the NIC link. I went to the DNS servers section and changed the DNS server to dc-1's private IP address. Doing this joins the domain of both VMs. I then clicked the save button.
</p>
<br />

<p>
<img width="1512" height="400" alt="image" src="https://github.com/user-attachments/assets/6ba1e783-fd9a-4a55-873c-eda07374e3ff" />

</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="1762" height="583" alt="image" src="https://github.com/user-attachments/assets/7098dbcb-ff0e-4400-9d44-3cd12586ba8f" />

</p>
<p>
I then logged into client-1's VM in order to ping dc-1. 
<br />

<p>
<img width="1177" height="542" alt="image" src="https://github.com/user-attachments/assets/4f83d757-ac11-45c2-b74d-4acfa133de1b" />

</p>
<p>
I opened Powershell in client-1 and pinged the private IP address of dc-1. 
</p>
<br />

<p>
<img width="1186" height="782" alt="image" src="https://github.com/user-attachments/assets/1d65c6f0-3b67-45d7-a991-f3980bd60284" />

</p>
<p>
Private IP address should show 10.0.0.4 after using ipconfig /all. This concludes the VM setup for the Active Directory project.
</p>
<br />
