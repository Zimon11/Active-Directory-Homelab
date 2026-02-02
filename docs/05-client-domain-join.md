
⬅️ [Previous: Active Directory Installation and Configuration](04-ad-installation-configuration.md) | [Next: Troubleshooting ➡️](06-troubleshooting.md)

# 💻 Client Configuration and Domain Join

### Step 4: Set up client computer and join it into domain
![Screenshot](../screenshots/Configuring-Windows-Client/Configure-WC1.png)
- Installed Windows 11 client and configured its DNS to point to the Domain Controller’s IP address in preparation for domain joining.

![Screenshot](../screenshots/Configuring-Windows-Client/Configure-WC2.png)
- Verified DNS communication between the client and the Domain Controller.

![Screenshot](../screenshots/Configuring-Windows-Client/Configure-WC3.png)
- Renamed the client computer for proper identification before joining the domain.

![Screenshot](../screenshots/Domain-join/DomainJoin1.png)
- Navigated to the Settings>System>About>Advance System Settings.

![Screenshot](../screenshots/Domain-join/DomainJoin2.png)
- Selected the Domain option and entered the domain name adlab.local.

![Screenshot](../screenshots/Domain-join/DomainJoin3.png)
- Entered credentials of an account authorized to join computers to the domain.
- (For this lab, the built-in Administrator account was used. In production environments, a delegated account is recommended.)

![Screenshot](../screenshots/Domain-join/DomainJoin4.png)
- The client computer was successfully joined to the domain.


⬅️ [Previous: Active Directory Installation and Configuration](04-ad-installation-configuration.md) | [Next: Troubleshooting ➡️](06-troubleshooting.md)
