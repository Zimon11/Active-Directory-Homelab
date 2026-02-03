⬅️ [Previous: Groups and GPO](06-groups-and-gpo.md) | [Next: Lessons Learned➡️](08-lessons-learned.md)

# 🛠️ Troubleshooting

### Step 6: Domain user logon test and troubleshooting
![Screenshot](../screenshots/Troubleshoot/Troubleshoot8.jpg)
- Attempted to log in using the domain user created in Step 3 [Active Directory Installation and configuration](04-ad-installation-configuration.md).

![Screenshot](../screenshots/Troubleshoot/Troubleshoot9.jpg)
- The login failed with a Remote Desktop Services-related error due to missing user logon rights.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot10.jpg)
- To fix the issue I logged-in in the client using either Local Administrator or the Domains Administrator account in this picture I logged-in as a Local Administrator.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot1.png)
- Opened the Local Security Policy console using secpol.msc.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot2.png)
- Added the Domain users group in the **Allow Log on locally** policy.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot3.png)
- Entered domain administrator credentials to apply the change.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot5.png)
- Also added the same group in **Allow log on through Remote Desktop Services** policy.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot6.png)
- Applied the changes by typing the command **gpupdate /force** in the command line then restart.

![Screenshot](../screenshots/Troubleshoot/Troubleshoot7.png)
- Logged-in again using the Domain user account and it worked.

### ⚠️Note: This local configuration was applied only for troubleshooting. In the last steps, logon rights was centrally managed using Group Policy and security groups to follow enterprise best practices.

⬅️ [Previous: Groups and GPO](06-groups-and-gpo.md) | [Next: Lessons Learned➡️](08-lessons-learned.md)