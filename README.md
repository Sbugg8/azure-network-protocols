<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://youtu.be/Mu_2UnOdVHM?si=7-FO4Sj0c4VwUOfq)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Sharing out resources over the network
- Creating File Shares to allow: Read, Write, or Deny access to individual groups and users.



<h2>Actions and Observations</h2>

Create some sample file shares with various permissions. On DC, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting”.

![image](https://github.com/user-attachments/assets/af561760-53de-422c-bc9b-7c3f1232526e)


Once the 4 folders are created, we will then set up permissions for each folder. The following permissions have been set : 
Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”. In order to do this, right click properties -> sharing -> share -> type Domain users and then select to add.

![image](https://github.com/user-attachments/assets/a87d2566-0bdd-4040-8991-3a37e159b0b3)

 Next, attempt to access file shares as a normal user.
On Client server, navigate to the shared folder (start, run, \\dc-1) and try to access the folders you just created.

![image](https://github.com/user-attachments/assets/3f3907e8-3f61-4769-ba55-b78f7e4a532e)

Click on each folder and observe the things you can and cannot do. You will note that on the "read-access" folder, it will only let you read what is inside of the folder but will not make you add or make changes. These prompts are going to work differently in each folder since each folder has different permissions. For example, we have given the "write-access" folder permissions to read/write and therefore when we access it, we can make add writng if we needed to. This system allows for files to be shared over the network while offering organization to give access to either a specific group or an individual.

![image](https://github.com/user-attachments/assets/e13873e2-b41c-4b45-ab7e-e25dc9edfd06)

