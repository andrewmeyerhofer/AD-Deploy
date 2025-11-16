<p align="center">
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/08b4eda2-473f-4cc3-a35e-44f13257e740" />


</p>

<h1>Deploying Active Directory</h1>
Add Summary After<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 (24H2)


<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1313" height="972" alt="image" src="https://github.com/user-attachments/assets/a53815b8-1bee-454d-95e0-4c285aa3e484" />

</p>
<p>
I started by logging into the dc-1 VM (I created it in the "VM Creation in Microsoft Azure" project). The Server Manager dashboard opened upon logging in. 
</p>
<br />

<p>
<img width="1232" height="811" alt="Screenshot 2025-09-17 101953" src="https://github.com/user-attachments/assets/4940bb0e-071b-4ce6-bc99-d9412cd15f56" />


</p>
<p>
Next, I clicked the "Add Roles and Features" button which opened the Add Roles and Features wizard. I selected the next button a couple times until I reached the server roles section. Once there, I checked the box for Active Directory Domain Services.
</p>
<br />

<p>
<img width="1133" height="765" alt="Screenshot 2025-09-17 102309" src="https://github.com/user-attachments/assets/be3ad7f1-3d28-48cd-85af-956d1302b1fb" />


</p>
<p>
I then clicked the next button until I reached the confirmation page, where I checked the restart if required box. I finished by clicking the install button. 
</p>
<br />

<p>
<img width="816" height="445" alt="Screenshot 2025-09-17 102717" src="https://github.com/user-attachments/assets/4349f40b-36af-4670-baed-1ba64631f5fc" />


</p>
<p>
After the installation was complete, I clicked the flag icon in the top right of server manager and selected the option to promote dc-1 to a domain controller. 
</p>
<br />

<p>
<img width="950" height="716" alt="Screenshot 2025-09-17 110518" src="https://github.com/user-attachments/assets/5f28f43d-d898-4259-94d7-3a6b66fde53c" />


</p>
<p>
Once the configuration wizard opened, I selected "Add a new forest" as the deployment operation. I entered mydomain.com as the root domain name. I also entered a password for the directory services restore mode.
</p>
<br />

<p>
<img width="941" height="688" alt="Screenshot 2025-09-17 111059" src="https://github.com/user-attachments/assets/5b69b61b-c6e7-4c75-9988-fabdab8e0dbd" />


</p>
<p>
Under DNS options, I made sure to leave the DNS delegation box unchecked. 
</p>
<br />

<p>
<img width="943" height="690" alt="Screenshot 2025-09-17 111411" src="https://github.com/user-attachments/assets/58680aca-d191-4ad3-8bd0-3f06c9c989cf" />


</p>
<p>
I then clicked next until I reached the Prerequisites Check section, where I clicked the install button. After clicking install, the dc-1 VM restarted itself. Now that dc-1 was a domain controller, I had to include mydomain.com\ before my username while logging into the VM. 
</p>
<br />

<p>
<img width="845" height="799" alt="Screenshot 2025-09-18 110738" src="https://github.com/user-attachments/assets/2b31fc67-4f8d-4771-8bc3-5b93885bca15" />


</p>
<p>
Once dc-1 finished logging in, I opened Windows administrative tools and selected Active Directory Users and Computers.
</p>
<br />

<p>
<img width="974" height="667" alt="Screenshot 2025-09-18 110928" src="https://github.com/user-attachments/assets/2e58bd87-15c8-4373-a82c-7f25380be6c9" />

</p>
<p>
Within ADUC, I right-clicked the mydomain.com dropdown and selected New, then Organizational Unit.
</p>
<br />

<p>
<img width="941" height="668" alt="Screenshot 2025-09-18 111046" src="https://github.com/user-attachments/assets/49ec4d6d-6ea5-42a5-8dfb-3bceeb731bcd" />


</p>
<p>
I was then able to create a new Organizational Unit named _Employees (The _ makes it appear at the top of the list, so it's easy to find).
</p>
<br />

<p>
<img width="930" height="656" alt="Screenshot 2025-09-18 111217" src="https://github.com/user-attachments/assets/973a64e9-fd58-403a-b42f-6bcb866cfc1b" />


</p>
<p>
After pressing ok for _Employees, I created another organizational unit named _Admins. I then right-clicked the mydomain.com dropdown and selected the refresh option.
</p>
<br />

<p>
<img width="947" height="667" alt="Screenshot 2025-09-18 111403" src="https://github.com/user-attachments/assets/d8dacb47-119e-4a86-89a0-474fe1b88f93" />


</p>
<p>
Next, I right-clicked in the _Admins folder and selected the option to create a new user. I named the user Jane Doe and added basic information for her admin account. After clicking next, I inputted a password for Jane and selected the check-box for the password to never expire. 
</p>
<br />

<p>
<img width="933" height="657" alt="Screenshot 2025-09-18 111636" src="https://github.com/user-attachments/assets/d82d0ae6-c356-490b-b94f-3248d27d89bc" />


</p>
<p>
After clicking the next button again, I clicked Finish to finalize the user creation. 
</p>
<br />

<p>
<img width="1283" height="668" alt="Screenshot 2025-09-18 111939" src="https://github.com/user-attachments/assets/e6ae2997-930c-49a5-8e71-9f08562fdaa0" />


</p>
<p>
Next, I needed to actually make Jane's account an admin account. In ADUC, I located her account in the _Admins folder and right-clicked it to select properties. In the properties menu, I selected the tab "Member Of" then clicked the add button. I entered Domain Admins as the group then clicked ok. Finally, I clicked the Apply button in the properties menu and Jane was officially added as a Domain Admin. 
</p>
<br />

<p>
<img width="562" height="686" alt="image" src="https://github.com/user-attachments/assets/2251ab28-b9c4-4691-9128-af6fbcb69053" />


</p>
<p>
I then logged out of the dc-1 VM and logged back in as jane_admin. 
</p>
<br />

<p>
<img width="1580" height="901" alt="image" src="https://github.com/user-attachments/assets/ffb9ea8e-c9d9-4100-b8d0-5c04c3f3032d" />


</p>
<p>
I also used Janes credentials to join the domain, and restarted the client-1 VM.
</p>
<br />

<p>
<img width="957" height="696" alt="image" src="https://github.com/user-attachments/assets/b382fb5d-ef07-46d1-9ca6-fb50f2216fef" />


</p>
<p>
I dc-1 as jane...
</p>
<br />

<p>
<img width="933" height="657" alt="image" src="https://github.com/user-attachments/assets/78c2947c-e9fb-472b-8966-4bfa7fb064d9" />


</p>
<p>
Created a new organizational unit for clients, then I drag and dropped client-1 into the new clients folder.
</p>
<br />

<p>
<img width="1272" height="903" alt="image" src="https://github.com/user-attachments/assets/6f47c92c-b974-4d4b-b25a-7caaf5f3a2fa" />


</p>
<p>
I logged into Client-1 as Jane. I right clicked the start menu and went to system, then clicked remote desktop.
</p>
<br />

<p>
<img width="1263" height="930" alt="image" src="https://github.com/user-attachments/assets/bb642eb1-2371-4bfa-a110-de16fbadb451" />


</p>
<p>
After clicking the add button, I entered Domain Users as the object name then clicked OK.
</p>
<br />

<p>
<img width="413" height="82" alt="image" src="https://github.com/user-attachments/assets/36106281-3b4d-4d5a-8b3a-6c20367ade2f" />


</p>
<p>
I logged back into dc-1 as Jane.
</p>
<br />

<p>
<img width="1038" height="937" alt="image" src="https://github.com/user-attachments/assets/831c17e1-53b9-4855-bc2b-c3720a9541e9" />


</p>
<p>
I then pasted a script into Powershell that will create a bunch of new users. I also saved it to the VM desktop. I also changed the value for users (down to 100), and set the password.
</p>
<br />

<p>
<img width="933" height="648" alt="image" src="https://github.com/user-attachments/assets/b4f8966c-cb4a-4d78-bcf8-35c8d669c9d1" />



</p>
<p>
I opened up AD users and computers again, and went to the Employees folder.
</p>
<br />

<p>
<img width="562" height="678" alt="image" src="https://github.com/user-attachments/assets/37572902-82b3-4691-b6f5-7a5d24c73177" />


</p>
<p>
I picked the random user account cit.sel to user for testing. I logged out of Client-1 as Jane. Now lets simulate an account lock-out.
</p>
<br />

<p>
<img width="553" height="588" alt="image" src="https://github.com/user-attachments/assets/c47ce913-8a55-4b27-ab62-5f807f68b96b" />


</p>
<p>
Using cit.sel's account, I attempted to log into client one at least ten times with the wrong password. Since there is no group lock-out policy enabled, it still let me enter the account as normal once I put in the correct password.
</p>
<br />

<p>
<img width="931" height="651" alt="image" src="https://github.com/user-attachments/assets/368be591-7ca8-488b-b677-58947f8427ec" />


</p>
<p>
In the dc-1 vm using Jane's account... Using the run command I typed gpmc.msc to open group policy management.
</p>
<br />

<p>
<img width="1052" height="765" alt="image" src="https://github.com/user-attachments/assets/2f836830-2644-4049-b2cc-6ce37fe9711e" />


</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img width="993" height="772" alt="image" src="https://github.com/user-attachments/assets/c8546392-d72f-4c1c-a762-a0332c770918" />


</p>
<p>
Set to 6 invalid logout attempts.
</p>
<br />

<p>
<img width="723" height="403" alt="image" src="https://github.com/user-attachments/assets/cf5d06cd-57e9-4a89-90be-361eb10978e0" />


</p>
<p>
Logged into client-1 as Jane and opened command prompt.
</p>
<br />

<p>
<img width="682" height="178" alt="image" src="https://github.com/user-attachments/assets/7700bcbf-1e2a-402a-92bc-ab4569b6bac1" />


</p>
<p>
I then went logged into client-1 with the wrong password six times as cit.sel, and got an error message.
</p>
<br />

<p>
<img width="957" height="713" alt="image" src="https://github.com/user-attachments/assets/0716ff42-199d-4bd6-b8cb-323cda2655f2" />


</p>
<p>
In dc-1 as Jane, I went to AD users and computers and double clicked cit.sel's user profile. Under properties, I went to the Account tab and clicked the unlock account check box. I then clicked apply and okay.
</p>
<br />

<p>
<img width="1553" height="791" alt="image" src="https://github.com/user-attachments/assets/6fcf871a-c5a4-4f29-bda8-8d8537348a70" />


</p>
<p>
I then logged back into client-1 with cit.sel and everything worked properly.
</p>
<br />

<p>
<img width="927" height="658" alt="image" src="https://github.com/user-attachments/assets/e9311963-0b0c-46a9-92bd-c041cebdc085" />


</p>
<p>
Next, I deisabled cit.sel's account as Jane.
</p>
<br />

<p>
<img width="685" height="157" alt="image" src="https://github.com/user-attachments/assets/2717a059-c9b8-4aad-9f61-6cd9acbcca06" />


</p>
<p>
After trying to login as cit.sel on client-1, I get this error message. I then enabled the account on dc-1 and the account worked again.
</p>
<br />

<p>
<img width="977" height="681" alt="image" src="https://github.com/user-attachments/assets/00879558-9690-40a4-9440-7e65a7014639" />


</p>
<p>
I then opened event viewer on dc-1 and clicked the security drop down under windows logs. Here I can see all of the logon attempts. 
</p>
<br />

<p>
<img width="1392" height="945" alt="image" src="https://github.com/user-attachments/assets/3e8a791b-f26c-4157-b3b3-5655525113c5" />


</p>
<p>
By right clicking the security tab, I clicked the find option and searched for cit.sel. I then clicked the next button to view some of the failed logins.
</p>
<br />

<p>
<img width="1835" height="945" alt="image" src="https://github.com/user-attachments/assets/e7329f15-d45b-4e77-87e2-a62ed48567d3" />


</p>
<p>
I then logged into client-1 as cit.sel and opened event viewer as an admin. I then supplied Jane's credentials so I would have access to the security files. Here I can view the specific login failures for this VM from when I failed to login 6 times. This concludes the AD deployment project.
</p>
<br />
