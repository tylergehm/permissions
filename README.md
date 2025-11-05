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
