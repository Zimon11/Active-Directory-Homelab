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
- Filled up the users information for their user account.

![Screenshot](screenshots/Creating-OUs/OU-Creation7.png)
- Created a strong password for the User.
- Temporarily disabled **"User must change password at next logon"** for lab purposes(It's not recommended).

![Screenshot](screenshots/Creating-OUs/OU-Creation8.png)
- This image shows that the user is successfully created.
---
### Step 4: Set up client computer and join it into domain
![Screenshot](screenshots/Configuring-Windows-Client/Configure-WC1.png)
- Installed Windows 11 client and configured its DNS to point to the Domain Controller’s IP address in preparation for domain joining.

![Screenshot](screenshots/Configuring-Windows-Client/Configure-WC2.png)
- Verified DNS communication between the client and the Domain Controller.

![Screenshot](screenshots/Configuring-Windows-Client/Configure-WC3.png)
- Renamed the client computer for proper identification before joining the domain.

![Screenshot](screenshots/Domain-join/DomainJoin1.png)
- Navigated to the Settings>System>About>Advance System Settings.

![Screenshot](screenshots/Domain-join/DomainJoin2.png)
- Selected the Domain option and entered the domain name adlab.local.

![Screenshot](screenshots/Domain-join/DomainJoin3.png)
- Entered credentials of an account authorized to join computers to the domain.
- (For this lab, the built-in Administrator account was used. In production environments, a delegated account is recommended.)

![Screenshot](screenshots/Domain-join/DomainJoin4.png)
- The client computer was successfully joined to the domain.

### Step 4.1: Domain user logon test and troubleshooting
![Screenshot](screenshots/Troubleshoot/Troubleshoot8.jpg)
- Attempted to log in using the domain user created in Step 3.1.

![Screenshot](screenshots/Troubleshoot/Troubleshoot9.jpg)
- The login failed with a Remote Desktop Services-related error due to missing user logon rights.

![Screenshot](screenshots/Troubleshoot/Troubleshoot10.jpg)
- To fix the issue I logged-in in the client using either Local Administrator or the Domains Administrator account in this picture I logged-in as a Local Administrator.

![Screenshot](screenshots/Troubleshoot/Troubleshoot1.png)
- Opened the Local Security Policy console using secpol.msc.

![Screenshot](screenshots/Troubleshoot/Troubleshoot2.png)
- Added the Domain users group in the **Allow Log on locally** policy.

![Screenshot](screenshots/Troubleshoot/Troubleshoot3.png)
- Entered domain administrator credentials to apply the change.

![Screenshot](screenshots/Troubleshoot/Troubleshoot5.png)
- Also added the same group in **Allow log on through Remote Desktop Services** policy.

![Screenshot](screenshots/Troubleshoot/Troubleshoot6.png)
- Applied the changes by typing the command **gpupdate /force** in the command line then restart.

![Screenshot](screenshots/Troubleshoot/Troubleshoot7.png)
- Logged-in again using the Domain user account and it worked.

### ⚠️Note: This local configuration was applied only for troubleshooting. In later steps, logon rights will be centrally managed using Group Policy and security groups to follow enterprise best practices.
---

## 📚 What I Learned
