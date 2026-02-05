⬅️ [Previous: Groups and GPO](06-groups-and-gpo.md) | [Next: Lessons Learned➡️](08-lessons-learned.md)

# Step 6: 🛠️ Testing and Troubleshooting

### Step 6.1: Test Domain user logon
![Screenshot](../screenshots/Troubleshoot/Troubleshoot8.jpg)
- Attempted to log in using the domain user created in Step 3 [Active Directory Installation and configuration](04-ad-installation-configuration.md).
- Logged in using an IT department domain user account.
- The target machine was IT workstation.

### Step 6.2: Issue Encountered: Remote Desktop Service Logon Error
![Screenshot](../screenshots/Troubleshoot/Troubleshoot9.jpg)
- Login attempt failed with a Remote Desktop Services–related error, even though the user was logging in locally.
#### Problem Cause
- Domain users was not included in allow logon policy and Remote Desktop services.
- Allow logon policy on a freshly installed server may not automatically enabled.
#### Why this happens?
- Fresh installation of server may not automatically include domain users logon rights

### Step 6.3: Troubleshooting and Temporarily fixed the Domain logon issue
![Screenshot](../screenshots/Troubleshoot/Troubleshoot10.jpg)
- To fix the issue I logged-in in the client using Local Administrator to perform troubleshooting.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot1.png)
- Opened the Local Security Policy console using secpol.msc.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot2.png)
- Added the Domain users group in the **Allow Log on locally** policy.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot3.png)
- Entered domain administrator credentials to apply the change.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot5.png)
- Added the Domain users group in **Allow log on through Remote Desktop Services** policy.

### Step 6.4: Validation and policy application
![Screenshot](../screenshots/Troubleshoot/Troubleshoot6.png)
- Applied the changes by typing the command **gpupdate /force** in the command line then restart the machine.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot7.png)
- Successfully Logged-in using the Domain user account.
- The issue is now confirmed solve.

### ⚠️Note: This local configuration was applied only for troubleshooting. In the last steps [Groups and GPO](06-groups-and-gpo.md), logon rights was centrally managed using Group Policy and security groups to follow enterprise best practices this step is how do permanently fix the issue and the most efficient way to solve the problem. 

⬅️ [Previous: Groups and GPO](06-groups-and-gpo.md) | [Next: Lessons Learned➡️](08-lessons-learned.md)