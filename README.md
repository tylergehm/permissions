  <img src="https://raw.githubusercontent.com/tylergehm/permissions/main/permissions.jpg" alt="GitHub banner" style="max-width:100%;height:auto;" />
</p>
<h1>Active Directory File Shares: Mastering Permissions with Security Groups</h1>
This Azure Active Directory project explores role-based access control by creating shared folders with varying permissions assigned to domain-wide and specialized security groups. A standard user tests access from a client machine, verifying read-only, read/write, and restricted behaviors. A dedicated security group is then created and granted full control over a previously inaccessible folder; after adding the user to this group and re-authenticating, access is successfully granted, illustrating how Active Directory groups centrally manage file share permissions in an enterprise environment.<br />
</p>


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 11 Pro (21H2)
- Windows 11 Home (Host Machine)

  <h2>Prequisites</h2>
- Windows Server 2025 Virtual Machine configured as Domain Controller
- Windows 11 Pro Virtual Machine configured as client

For additional information on how these virtual machines were set up, visit [Configuring Active Directory within Azure VMs](https://github.com/tylergehm/configure-ad)


<h2>Project Steps</h2>

- Step 1 - Log in to DC and Client VMs
- Step 2 - Create folders on C:\ drive of Domain Controller
- Step 3 - Set Permissions
- Step 4 - Attempt to access file shares as a normal user
- Step 5 - Create a Security Group
- Step 6 - Observe file access as a normal user and user in security group

<h2>- Step 1 - Log in to DC and Client VMs</h2>
Note:
This project uses a Domain Controller virtual machine and a client virtual machine that were previously set up on the project: </p>
[Configuring Active Directory within Azure VMs](https://github.com/tylergehm/configure-ad) </p>

The project will begin logged in to both the Domain Controller virtual machine and the Client-1 virtual machine. </p>

<h2>Step 2 - Create folders on C:\ drive of Domain Controller</h2>

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e273c8dc-083c-47ea-b014-7add153d73e6" />

In the Domain Controller VM, use the file explorer to open the C:\ drive. In this drive there will be four folders to create: "Read-Access", "Write-Access", "No-Access", and "Accounting". </p>

<img width="1400" height="738" alt="image" src="https://github.com/user-attachments/assets/25c8b666-5cb5-4244-91ce-9d3a20d60d43" /> </p>

The four new folders have been created and named appropriately. </p>

<img width="1389" height="731" alt="image" src="https://github.com/user-attachments/assets/10217f40-744e-46b8-b457-186696460540" />

Each of the folders will be set with properties according to their name. The "Read-Access" folder will be given the permission to Read-Only. To set this up, right-click on the folder and click on "Properties". </p>

<img width="480" height="590" alt="image" src="https://github.com/user-attachments/assets/5140e9fb-1dc0-4bb5-a559-60003f868f96" /> </p>

Once inside the folder Properties, click on the tab "Sharing" then click the button that says "Share..." </p>

<img width="700" height="587" alt="image" src="https://github.com/user-attachments/assets/aed3221d-b1af-41e3-90b0-dc71cbedb4d9" /> </p>

In the text box, type "Domain Users" and click "Add" to give folder permission to all domain users. </p>

<img width="696" height="590" alt="image" src="https://github.com/user-attachments/assets/66d47ba7-86f4-439f-b0c0-e44659ce2f00" /> </p>

Verify that the Permission Level is set to "Read", then click Apply. This gives users access to the folder, but can only view the contents inside and cannot alter them in any way. </p>

<img width="708" height="593" alt="image" src="https://github.com/user-attachments/assets/d197d6ec-cd6e-4eb9-9647-9dd865eb162a" /> </p>

This next screen verifies that the folder gives Read-Only permission. Click "Done". </p>

<img width="706" height="580" alt="image" src="https://github.com/user-attachments/assets/2702d89e-f811-4aeb-9702-cf7705033d98" /> </p>

This process is repeated for the "Write-Only" folder. Notice that the Permission Level is Read/Write. This gives users access to view the contents of the folder and to edit the files contained within. </p>

<img width="702" height="589" alt="image" src="https://github.com/user-attachments/assets/23d113e2-1b20-4585-83b5-408d10628c50" />

For the "No-Access" folder, the Read/Write permissions are granted to Domain Admins. This means if a standard domain user tries to access the folder then they will be denied access. </p>

<h2>Step 3 - Set Permissions</h2>

<img width="1913" height="1074" alt="image" src="https://github.com/user-attachments/assets/7312b5cc-1db3-4715-a960-dbb8049b7fff" /> </p>

Next, the Client-1 VM will be logged into as a normal domain user. Open the file explorer and type in the address bar "\\dc-1". This will give access to the folders that have been shared by the Domain Controller VM on the network. </p>

<img width="1408" height="742" alt="image" src="https://github.com/user-attachments/assets/0199b600-4147-4a5c-83e7-09b310a10061" /> </p>

The file explorer is now viewing the shared folders in the "\\dc-1" network file sharing. Next, the user will attempt to open the folders. </p>

<img width="1408" height="742" alt="image" src="https://github.com/user-attachments/assets/a1fe0dfb-4c49-408d-95f6-18acda6013a6" /> </p>

The standard domain user was able to access the "Read-Only" folder because all Domain Users were granted permission. </p>

<img width="1400" height="734" alt="image" src="https://github.com/user-attachments/assets/9ba5e901-9662-4984-aae8-fc2e47a6426c" /> </p>

When attempting to create a file in the "Read-Only" folder, permission was denied because Domain Users have access to only view files. </p>

<img width="1408" height="742" alt="image" src="https://github.com/user-attachments/assets/c67b82b0-2735-413a-badd-36a80bffd781" /> </p>

The standard domain user was able to access the "Write-Only" folder because all Domain Users were granted permission to read and write files. </p>

<img width="1391" height="735" alt="image" src="https://github.com/user-attachments/assets/6aca6731-5bb4-4954-a52d-e48a78559be1" /> </p>

A text document was successfully created inside the folder because all Domain Users have access to view and create/edit files within the shared folder. </p>


<img width="1406" height="741" alt="image" src="https://github.com/user-attachments/assets/f332ff21-1945-4c68-87e7-49d6e6fc4b86" /> </p>

When attempting to open the "No-Access" folder, the standard user was denied because this folder has permissions set for only Domain Admins to have access. </p>















