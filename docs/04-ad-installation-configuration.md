⬅️ [Previous: Installation](03-installation.md) | [Next: Client Domain join ➡️](05-client-domain-join.md)

# 🧩 Active Directory Configuration

### Step:3 Installing Active Directory Domain Services
![Screenshot](../screenshots/AD_DS-Installation/AD-Installation-2.png)
- Selected the role Active Directory Domain Services.

![Screenshot](../screenshots/AD_DS-Installation/AD-Installation-4.png)
- Successfully installed ADDS into the server.

### Step:3.1 Promoting the server to Domain Controller
![Screenshot](../screenshots/DC-Promote/DC-promote2.png)
- Promoted the server to a Domain Controller and created a new forest named **adlab.local**.

![Screenshot](../screenshots/DC-Promote/DC-promote3.png)
- Configured the server to install and integrate DNS services with Active Directory.

![Screenshot](../screenshots/DC-Promote/DC-promote4.png)
- Set the domain and NetBIOS name for the Active Directory environment.

![Screenshot](../screenshots/DC-Promote/DC-promote5.png)
- Completed the prerequisites check and verified system readiness before finalizing the promotion.
- The DNS delegation warning appeared because this is a new forest with no existing parent DNS zone. This is expected behavior and does not affect functionality.

### Step 3.2: Post-Installation Verification and DNS Reconfiguration
![Screenshot](../screenshots/DC-Promote/ServerManagerUI.png)
- Verified successful installation and promotion of the server by confirming that Active Directory Domain Services and DNS are both running with healthy status in Server Manager.

![Screenshot](../screenshots/DC-Promote/DNS-reconfigure.png)
- Reconfigured the server’s DNS settings to point to its own IP address.
- This ensures the Domain Controller uses itself as the primary DNS server, which is required for proper Active Directory functionality and domain name resolution.

![Screenshot](../screenshots/DC-Promote/DNS-test.png)
- Tested DNS functionality by resolving the domain name to confirm proper name resolution.

### Step 3.3: Creating Organizational Units (OUs) separated by Department
![Screenshot](../screenshots/Creating-OUs/OU-Creation2.png)
- Created an OU for Admins it separated from the other departments.
- Admins OU is separate for privileged accounts.
- Checked the **"Protect from accidental deletion"** to prevent it from deleting accidentally.

![Screenshot](../screenshots/Creating-OUs/OU-Creation4.png)
- Created each departments OUs: HR, IT, and Finance.
- Each department contains Users and Computers sub-OUs for better organization and security management.

### Step 3.4: Creating User for the User OU
![Screenshot](../screenshots/Creating-OUs/OU-Creation5.png)
- Create a User for the IT Department.

![Screenshot](../screenshots/Creating-OUs/OU-Creation6.png)
- Filled up the users information for their user account.

![Screenshot](../screenshots/Creating-OUs/OU-Creation7.png)
- Created a strong password for the User.
- Temporarily disabled **"User must change password at next logon"** for lab purposes(It's not recommended).

![Screenshot](../screenshots/Creating-OUs/OU-Creation8.png)
- This image shows that the user is successfully created.


⬅️ [Previous: Installation](03-installation.md) | [Next: Client Domain join ➡️](05-client-domain-join.md)
