<h1>Active Directory Home Lab</h1>


 ### [YouTube Demonstration (@00:00)](https://youtu.be/wYRdlW8A7tQ)
<h2>Step 1 Create a New Virtual Machine </h2>

1. Open VMware Workstation.
Click "Create a New Virtual Machine" and select "Typical" configuration.
Browse and select the Windows Server 2022 ISO file.
Set up the virtual machine name and location.
Allocate resources:
Memory: At least 4GB for smooth performance.
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
-Set the Administrator password during installation.
</b>
<br />
<br />
<h2>Step 3: Configure Windows Server 2022</h2>
1.Change Computer Name

Right-click This PC > Properties > Advanced System Settings > Computer Name.
Rename the computer to something meaningful (e.g., ADSERVER).


