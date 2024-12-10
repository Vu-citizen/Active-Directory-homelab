<h1>Active Directory Home Lab</h1>


 ### [YouTube Demonstration (@00:00)](https://youtu.be/wYRdlW8A7tQ)
<h2>Step 1 Create a New Virtual Machine </h2>

1. Open VMware Workstation.
Click "Create a New Virtual Machine" and select "Typical" configuration.
Browse and select the Windows Server 2022 ISO file.
Set up the virtual machine name and location.
Allocate resources:
Memory: At least 2GB for smooth performance.
CPU: 2 processors recommended.
Disk Size: Allocate at least 60GB.
Configure Networking
</b>
<br />
<br />
2.Assign Two Network Adapters to the VM

<p align="center">
<img src="https://github.com/user-attachments/assets/3daf401f-a98d-4b6a-a8cf-67349405e6ac" height="50%" width="50%" alt="Image Analysis Dataflow"/>
</p>
In VMware Workstation, open the settings of your virtual machine.
Under Hardware, click Add > Network Adapter.
Ensure the VM has two network adapters:
Adapter 1: NAT (for internet access).
Adapter 2: Host-only or Custom network (for the internal network).
Customize the Network
</b>
<br />
<br />
<p align="center">
<img src="https://github.com/user-attachments/assets/89e7b338-4495-4abc-b4fd-e271bf020cae" height="50%" width="50%" alt="Image Analysis Dataflow"/>


3.Go to Edit > Virtual Network Editor in VMware Workstation.
Verify:
NAT is set up on one network 
Host-only is set up on another network (e.g., VMnet2) for the internal network.
</b>
<br />
<br />


<h2>Step 2: Install Windows Server 2022</h2>
</b>
<br />
<br />
Complete Installation
-Boot the VM and install Windows Server 2022.
<p align="center">
<img src="https://github.com/user-attachments/assets/6364bc7c-70b5-492c-acb1-4f93b8c091d6" height="50%" width="50%" alt="Image Analysis Dataflow"/>

 -Choose Desktop Experience for a graphical interface.
 <p align="center">
<img src="https://github.com/user-attachments/assets/69305a33-2384-444c-a35a-041142edf01c" height="50%" width="50%" alt="Image Analysis Dataflow"/>

-Set the Administrator password during installation.
</b>
<br />
<br />
<h2>Step 3: Configure Windows Server 2022</h2>
1.Change Computer Name
<br />
<img src="https://github.com/user-attachments/assets/d134c317-4702-4750-a4f1-2a789383d8e6" height="50%" width="50%" alt="Image Analysis Dataflow"/>
</b>
<br />
<br />
Right-click start> system > rename this PC .
Rename the computer to something meaningful like DC(domain controller.

</b>
<br />
<br />
2. Set a Static IP Address in the internal network
<br />
 <p align="center">
<img src="https://github.com/user-attachments/assets/1e20788f-21f8-4b20-b3dd-5ee721a06880" height="50%" width="50%" alt="Image Analysis Dataflow"/>

  Open Network and Sharing Center.
Go to Change adapter settings > Right-click your network adapter > Properties.
Set a static IP (e.g., 172.16.0.1), Subnet Mask  255.255.255.0, Default Gateway, and DNS Server (use the same IP as the static IP(172.16.0.1) or using a loopback(127.0.0.1).

3.Install Roles and Features

Open Server Manager > Manage > Add Roles and Features.
Choose:

<img src="https://github.com/user-attachments/assets/c1f70be7-4b41-4cbd-a289-d3f0c339e096" height="50%" width="50%" alt="Image Analysis Dataflow"/>


Role-based or feature-based installation.
<img src="https://github.com/user-attachments/assets/9b342824-256a-4958-b6ad-5b5855bb187a" height="50%" width="50%" alt="Image Analysis Dataflow"/>
Active Directory Domain Services (AD DS) role.
Allow it to automatically install required features like DNS and Group Policy.
Promote to Domain Controller
![image](https://github.com/user-attachments/assets/11d8dc22-d53f-4a8f-8907-ef318fe685c3)

After installing AD DS, a notification in Server Manager will prompt you to promote the server to a domain controller.
Click Promote this server to a domain controller.
![image](https://github.com/user-attachments/assets/f0701f23-58e8-45a2-9092-2f7df29310cf)

Create a new forest (e.g., example.local).
Specify a Directory Services Restore Mode (DSRM) password.
Finish the wizard and reboot.

<h2>Step 3: Add Admin account , Install and Configure RAS (Remote Access Service)and enable NAT and Routing </h2>
1.Add Users and Computers

![image](https://github.com/user-attachments/assets/f7b8effd-c2e3-4f49-aac0-881b49cb7fb8)

In Active Directory Users and Computers, create organizational units (OUs), users, and computer accounts for practice.

2. Install and Configure RAS (Remote Access Service)
-Open Server Manager > Manage > Add Roles and Features.
-Choose:
--Role-based or feature-based installation.
-Remote Access role.
![image](https://github.com/user-attachments/assets/d4d7e8f6-04d3-488b-a757-9aa2ded8070b)

On the next screen, select Routing and continue with the installation by clicking Next until installation is complete.

4. Enable NAT and Routing
 ![image](https://github.com/user-attachments/assets/7ce97201-8edf-4553-ac1a-7677d80cad62)
After installation, go to Tools > Routing and Remote Access in Server Manager.
![image](https://github.com/user-attachments/assets/eba179cc-ee1f-445e-afcc-a3099176af01)

Right-click your server name and select Configure and Enable Routing and Remote Access.
In the wizard:
Choose Network Address Translation (NAT).
![image](https://github.com/user-attachments/assets/6067c708-2f1d-487d-9e1b-bb1aac576513)

Select the network interface connected to the internet Network (Adapter 2).
Configure the NAT settings to allow clients on the private network to share the internet connection.


<h2>Step 4: Set Up DHCP Server </h2>
1. Install the DHCP Role
Go to Server Manager > Add Roles and Features.

![image](https://github.com/user-attachments/assets/84fa96ea-36be-45a5-b11b-3b1b1143be04)

Select the DHCP Server role and complete the installation by clicking Next until done.
2. Configure DHCP
![image](https://github.com/user-attachments/assets/3c738545-b5f5-4c05-b953-cc589596db56)

Open Tools > DHCP.
![image](https://github.com/user-attachments/assets/47f32c04-77ca-4844-b7ce-d81a88793e2f)

Right-click your server name and select New Scope.
![image](https://github.com/user-attachments/assets/afab5c8f-5882-4c25-83bc-9b75026b3e7c)

Configure the scope:
Start IP: 172.16.0.100.
End IP: 172.16.0.200.
Subnet Mask: 255.255.255.0.  
![image](https://github.com/user-attachments/assets/c49cc3bf-a00a-44c8-b940-11c08268416d)

Default Gateway: 172.16.0.1 (IP of the internal network adapter on the domain controller).
![image](https://github.com/user-attachments/assets/5a5e3ed7-9c88-4708-9952-c4308292d4be)

DNS Server: 172.16.0.1 (or the domain controller’s IP my case 192.168.26.138).
![image](https://github.com/user-attachments/assets/0e0808ea-aee7-49fe-b33f-a8191b48c81a)

next , set up router in server option-
![image](https://github.com/user-attachments/assets/c98447b6-87ef-43bf-8c54-c42354a7efbd)

Activate the scope after configuration by authorized and refresh .

<h2>Step 5: Create a user and connect Client Machines</h2>

![image](https://github.com/user-attachments/assets/e8fe84f6-a6c2-42fa-a04b-7245b7042244)

Set Up Clients- This is similar to adding admin account but we will be make a new organisation unit called _USER where we will put the user in.
![image](https://github.com/user-attachments/assets/0c4edc5d-25b1-40c7-b8bc-64e74663abee)

![image](https://github.com/user-attachments/assets/1f06cdf7-e3e2-40eb-8f9f-9cd376ab2020)




Verify internet connectivity and domain login functionality from the client machine.
