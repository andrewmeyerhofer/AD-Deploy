<p align="center">
<img width="250" height="250" alt="image" src="https://github.com/user-attachments/assets/08b4eda2-473f-4cc3-a35e-44f13257e740" />


</p>

<h1>Deploying Active Directory</h1>
In this project, my main goals were to install and configure Active Directory Domain Services and simulate interactions between a domain contoller and a client on the domain. The initial setup for this project (creating the VMs and disabling the Windows Firewall) took place in the previous project titled "VM Creation in Microsoft Azure." This project is dense, so I provided a brief overview of what I accomplished below. <br />

<h2>Overview of Objectives</h2>

- Installation of AD Domain Services on dc-1 VM.
- Creation of a new domain: mydomain.com.
- Creation and configuration of a Domain Admin user.
- Creation of new organizational units within Active Directory Users and Computers (ADUC).
- Joining of client-1 VM to the domain.
- Remote Desktop setup on client-1.
- Creation of random user accounts using Powershell.
- Simulation of a user account lockout.
- Simulation of disabling a user account.
- Observation of Security logs.

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
I started by logging into the dc-1 VM. The Server Manager dashboard opened upon logging in. 
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
Next, I logged into the client-1 VM as myself in order to join it to the domain. Once in client-1, I selected System from the Windows start menu and chose the "Rename this PC (advanced)" option. I then clicked the change button in the Computer Name tab and chose the Member of a Domain option. I entered mydomain.com as the domain name then clicked ok. A login prompt then opened in which I entered Jane's credentials to authorize the joining of the domain. Finally, I got a message saying I was now part of mydomain.com, and I was prompted to restart the client-1 VM.
</p>
<br />

<p>
<img width="957" height="696" alt="image" src="https://github.com/user-attachments/assets/b382fb5d-ef07-46d1-9ca6-fb50f2216fef" />


</p>
<p>
Once client-1 fully restarted, I went back to dc-1 as Jane. In ADUC, I clicked on the Computers folder under mydomain.com. From there, I was able to see that client-1 was successfully added as a member of the domain. 
</p>
<br />

<p>
<img width="933" height="657" alt="image" src="https://github.com/user-attachments/assets/78c2947c-e9fb-472b-8966-4bfa7fb064d9" />


</p>
<p>
I then created a new organizational unit named _Clients for organizational purposes. I dragged client-1 from the Computers folder and dropped it into the _Clients folder, then clicked refresh.
</p>
<br />

<p>
<img width="1272" height="903" alt="image" src="https://github.com/user-attachments/assets/6f47c92c-b974-4d4b-b25a-7caaf5f3a2fa" />


</p>
<p>
Next, I logged back into client-1 as Jane. I right clicked the start menu and went to system, then clicked remote desktop. From there, I clicked the Remote Desktop users button.
</p>
<br />

<p>
<img width="1263" height="930" alt="image" src="https://github.com/user-attachments/assets/bb642eb1-2371-4bfa-a110-de16fbadb451" />


</p>
<p>
I then clicked the Add button and entered Domain Users as the object name. Once MYDOMAIN\Domain Users populated, I clicked the ok button.
</p>
<br />

<p>
<img width="413" height="82" alt="image" src="https://github.com/user-attachments/assets/36106281-3b4d-4d5a-8b3a-6c20367ade2f" />


</p>
<p>
Next, I went back to dc-1 as Jane with the intent of adding users to the _Employees OU. I started by searching for Powershell ISE in the Windows start menu. Once I found it, I right-clicked it and selected "Run as administrator."
</p>
<br />

<p>
<img width="1038" height="937" alt="image" src="https://github.com/user-attachments/assets/831c17e1-53b9-4855-bc2b-c3720a9541e9" />


</p>
<p>
Once I was in Powershell, I pasted a script (created by CourseCareers) that's purpose was to create a bunch of new users in the _Employees OU. In the top lines of the script, I changed the password and set the value for accounts created to 100. I also saved the script to the VM desktop.
</p>
<br />

<p>
<img width="933" height="648" alt="image" src="https://github.com/user-attachments/assets/b4f8966c-cb4a-4d78-bcf8-35c8d669c9d1" />



</p>
<p>
After successfully running the script, I opened up ADUC and went to the _Employees OU. The folder was now filled with 100 randomly generated user account names. 
</p>
<br />

<p>
<img width="562" height="678" alt="image" src="https://github.com/user-attachments/assets/37572902-82b3-4691-b6f5-7a5d24c73177" />


</p>
<p>
From the list, I picked the account cit.sel to use for testing. Using this account, the first thing I wanted to test was an account lock-out. I started by logging out of client-1 as Jane and logging back in as cit.sel. Once I confirmed that cit.sel could successfully login, I logged back out.
</p>
<br />

<p>
<img width="553" height="588" alt="image" src="https://github.com/user-attachments/assets/c47ce913-8a55-4b27-ab62-5f807f68b96b" />


</p>
<p>
Using cit.sel's account, I attempted to log into client-1 at least ten times with the wrong password. Since there was no group lock-out policy enabled, I was still able to enter the VM as normal once I put in the correct password.
</p>
<br />

<p>
<img width="931" height="651" alt="image" src="https://github.com/user-attachments/assets/368be591-7ca8-488b-b677-58947f8427ec" />


</p>
<p>
I then went back to dc-1 as Jane to change the group lock-out policy. Using Run from the Windows menu, I typed gpmc.msc to open Group Policy Management. Once the policy manager opened, I went to the Default Domain Policy section under mydomain.com. I then right-clicked and selected the edit option. 
</p>
<br />

<p>
<img width="1052" height="765" alt="image" src="https://github.com/user-attachments/assets/2f836830-2644-4049-b2cc-6ce37fe9711e" />


</p>
<p>
After clicking the edit button, the Group Policy Management Editor opened. I then selected the dropdown for Windows Settings, followed by Security Settings, then Account Lockout Policy. From there, I double-clicked the Account lockout duration option which opened up the Account lockout duration Properties menu. Under the Security Policy Settings, I chose the option to define the policy setting myself. I selected 30 minutes for the lockout duration, then clicked ok. 
</p>
<br />

<p>
<img width="993" height="772" alt="image" src="https://github.com/user-attachments/assets/c8546392-d72f-4c1c-a762-a0332c770918" />


</p>
<p>
The Policy Settings automatically updated once I entered the lockout duration, but I decided to change the lockout threshold from 5 to 6 invalid logon attempts. 
</p>
<br />

<p>
<img width="723" height="403" alt="image" src="https://github.com/user-attachments/assets/cf5d06cd-57e9-4a89-90be-361eb10978e0" />


</p>
<p>
I then logged into client-1 as Jane and opened command prompt in order to force group policy to update immediately. I used the command gpupdate /force, which successfully updated the group policy. 
</p>
<br />

<p>
<img width="682" height="178" alt="image" src="https://github.com/user-attachments/assets/7700bcbf-1e2a-402a-92bc-ab4569b6bac1" />


</p>
<p>
Now that a lockout policy was enabled, I logged out of client-1 as Jane and attempted to test the policy with cit.sel. I purposely inputted the wrong password six times, then got an error message telling me the account had been locked.
</p>
<br />

<p>
<img width="957" height="713" alt="image" src="https://github.com/user-attachments/assets/0716ff42-199d-4bd6-b8cb-323cda2655f2" />


</p>
<p>
In order to unlock the account, I went back to dc-1 as Jane and opened ADUC. From there, I double-clicked cit.sel's user profile in the _Employees OU. Under properties, I went to the Account tab and clicked the unlock account check box. I then clicked Apply and okay.
</p>
<br />

<p>
<img width="1553" height="791" alt="image" src="https://github.com/user-attachments/assets/6fcf871a-c5a4-4f29-bda8-8d8537348a70" />


</p>
<p>
I then logged back into client-1 as cit.sel (using the correct password) with no issues.
</p>
<br />

<p>
<img width="927" height="658" alt="image" src="https://github.com/user-attachments/assets/e9311963-0b0c-46a9-92bd-c041cebdc085" />


</p>
<p>
I also wanted to test what would happen if I disabled cit.sel's account. I went into ADUC as Jane, right-clicked cit.sel's account, then selected the Disable Account option.
</p>
<br />

<p>
<img width="685" height="157" alt="image" src="https://github.com/user-attachments/assets/2717a059-c9b8-4aad-9f61-6cd9acbcca06" />


</p>
<p>
I then attempted to login to client-1 as cit.sel, but I got an error message saying my account had been disabled. In order to fix this, I right-clicked the account in ADUC and selected the Enable Account option. 
</p>
<br />

<p>
<img width="977" height="681" alt="image" src="https://github.com/user-attachments/assets/00879558-9690-40a4-9440-7e65a7014639" />


</p>
<p>
Next, I opened Event Viewer on dc-1 and clicked the security drop-down under Windows logs. Here I could see all the logon attempts made recently.
</p>
<br />

<p>
<img width="1392" height="945" alt="image" src="https://github.com/user-attachments/assets/3e8a791b-f26c-4157-b3b3-5655525113c5" />


</p>
<p>
I then right-clicked the Security tab and clicked the Find option, which allowed me to search for cit.sel. After clicking Find Next, I was able to see all the failed logon attempts made by cit.sel specifically.
</p>
<br />

<p>
<img width="1835" height="945" alt="image" src="https://github.com/user-attachments/assets/e7329f15-d45b-4e77-87e2-a62ed48567d3" />


</p>
<p>
Finally, I logged into client-1 as cit.sel and opened Event Viewer as an admin. I then supplied Jane's credentials so I would have access to the security files. Here I could view the specific logon failures for this VM. This concludes the Deploying Active Directory project.
</p>
<br />
