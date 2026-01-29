# Project Title: Active Directory Homelab hands-on practice

## 📌 Objective
Build a virtualized Windows Domain Environment to practice the fundamentals of System administration and cybersecurity.

---

## 🖥️ Environment
- Windows Server 2025 (Domain Controller)
- Windows 11 (Client Computer)
- Hyper-V
- Active Directory, Group Policy
  
---

## 🏗️ Lab Architecture

---

## ⚙️ Implementation Summary
- Installed and Configure both Virtual Machine for Client(Windows 11) and Server(Windows Server 2025)
- Install Active Directory Domain Services.
- Promote Server to Domain Controller
- Create Organizational units and Users
- Joined a Client PC into Domain
- Applied Group Policies
---

## 📸 Screenshots and Steps
Below are the documented screenshots of Active Directory, Configurations, Security Practices. Each of these images are explained and also labeled for clarity.
### Step:1 Hyper-V and Virtual Machines Setup
![Screenshot](screenshots/HyperV-CreatingVm/Create-VirtualMachines.png)
- Set up the lab environment by creating two virtual machines (Server and Client).
- Allocated the systen resources and ready both of the virtual machine for installation.
  
![Screenshot](screenshots/HyperV-CreatingVm/VMs-Network-Adapter-1.png)
- Configured an external virtual switch in Hyper-V that will connect both VMs into the same network.

![Screenshot](screenshots/HyperV-CreatingVm/VMs-Network-Adapter-2.png)
- Ensured that both VMs are connected into the same switch for a proper communication between server and client.
---
### Step:2 Windows Server installation and configuration
![Screenshot](screenshots/Windows-Server-Installation/WS-Installation-1.png)
- Set a strong password for local Administrator.

![Screenshot](screenshots/Windows-Server-Installation/WS-Installation-2.png)
- Installed Windows Server 2025 on the server VM.

![Screenshot](screenshots/Configuring-Windows-Server/WS-Configure-3.png)
- Renamed the server into DC01 for better identification.

![Screenshot](screenshots/Configuring-Windows-Server/WS-Configure-1.png)
- Configured a static IP address on the Windows Server to ensure stable network identity.
- Temporarily assigned the router’s DNS server so the system could access the internet for updates and feature installation.

![Screenshot](screenshots/Configuring-Windows-Server/WS-Configure-2.png)
- Verified connectivity before installing Active Directory Domain Services.

### Step:2.1 Installing Active Directory Domain Services
![Screenshot](screenshots/AD_DS-Installation/AD-Installation-2.png)
- Selected the role Active Directory Domain Services.

![Screenshot](screenshots/AD_DS-Installation/AD-Installation-4.png)
- Successfully installed ADDS into the server.

### Step:2.2 Promoting the server to Domain Controller
![Screenshot](screenshots/DC-Promote/DC-promote2.png)
- Promoted the server to a Domain Controller and created a new forest named **adlab.local**.

![Screenshot](screenshots/DC-Promote/DC-promote3.png)
- Configured the server to install and integrate DNS services with Active Directory.

![Screenshot](screenshots/DC-Promote/DC-promote4.png)
- Set the domain and NetBIOS name for the Active Directory environment.

![Screenshot](screenshots/DC-Promote/DC-promote5.png)
- Completed the prerequisites check and verified system readiness before finalizing the promotion.
- The DNS delegation warning appeared because this is a new forest with no existing parent DNS zone. This is expected behavior and does not affect functionality.

### Step 2.3: Post-Installation Verification and DNS Reconfiguration
![Screenshot](screenshots/DC-Promote/ServerManagerUI.png)
- Verified successful installation and promotion of the server by confirming that Active Directory Domain Services and DNS are both running with healthy status in Server Manager.

![Screenshot](screenshots/DC-Promote/DNS-reconfigure.png)
- Reconfigured the server’s DNS settings to point to its own IP address.
- This ensures the Domain Controller uses itself as the primary DNS server, which is required for proper Active Directory functionality and domain name resolution.

![Screenshot](screenshots/DC-Promote/DNS-test.png)
- Tested DNS functionality by resolving the domain name to confirm proper name resolution.
---
### Step 3: Creating Organizational Units (OUs) separated by Department
![Screenshot](screenshots/Creating-OUs/OU-Creation2.png)
- Created an OU for Admins it separated from the other departments.
- Admins OU is separate for privileged accounts.
- Checked the **"Protect from accidental deletion"** to prevent it from deleting accidentally.

![Screenshot](screenshots/Creating-OUs/OU-Creation4.png)
- Created each departments OUs: HR, IT, and Finance.
- Each department contains Users and Computers sub-OUs for better organization and security management.

### Step 3.1: Creating User for the User OU
![Screenshot](screenshots/Creating-OUs/OU-Creation5.png)
- Create a User for the IT Department.

![Screenshot](screenshots/Creating-OUs/OU-Creation6.png)
- Filled up the users information for his/her user account.

![Screenshot](screenshots/Creating-OUs/OU-Creation7.png)
- Created a strong password for the User.
- Temporarily disabled **"User must change password at next logon"** for lab purposes(It's not recommended).

![Screenshot](screenshots/Creating-OUs/OU-Creation8.png)
- This image shows that the user is successfully created.
---
## 📚 What I Learned
