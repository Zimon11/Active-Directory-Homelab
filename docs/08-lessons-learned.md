
⬅️ [Previous: Testing and Troubleshooting](07-testing-and-troubleshooting.md) | [Next: Project Validation➡️](09-project-validation.md)

# 📚 Lessons Learned
### Active Directory Design
#### Importance of separating administrative accounts
- Separating the priveledged account from the non-priviledged can prevent the risk of Over Priveledged, also when applying GPOs it will be more efficient to do so because of the separation of accounts.

#### Benefits of making a deparment based OUs
- Structuring OUs to be a department based OUs make me much more familiar with a real enterprise environment. Also it helps me to manage permission separately from each deparment.

#### Benefits of separating the Groups OUs that handles permission and Users Group
- Structuring Groups OUs into 2 sub OUs create a separation between Handling permission(Access Groups) and Managing Groups(Global Groups users). This helps me to apply AGDLP model correctly.

#### Why using AGDLP is important when assigning permission
- Using this model help me to apply policy into each department efficiently, carefully and effectively.
---
### Group Policy Management
#### Difference between Centralized Control and Local Configuration
- Learning to configure centrally was much more reliable and efficient than configuring the device directly or locally, imagine if I have 1000 more devices and configure each devices locally then it is a disaster. Compare it when configuring it centrally using Group policy I just need to create and configure a Group Policy object and apply a permission and link it to a corresponding OU that need that specific permission.
---
### Troubleshooting skills
#### Importance of Event Viewer when troubleshooting authentication issue
- Before I'm just using different sources and AI about the issue that I encountered in lab but using Event Viewer in Windows helps me identify the issue much earlier combining it with the AI helps me troubleshoot the problem and understand the cause of the issue why it happen and how to fix it.

#### Understanding Windows logon types
- Windows authentication behavior depends on the logon type requested by the system. During testing, virtual machine console logins were recorded as Remote Interactive logons (Logon Type 10). Because the user did not have the required logon rights, access was denied even though the account existed in the domain.

#### Windows not accurately displaying the problem that the user was encountering
- Before I come up and finalize the cause of the issue, I encountered so many windows behavior when displaying an error message, I research about it and the sources said the same thing that Windows was not accurately mentioning the problem the user currently encountering and display only a fixed text like the RDP related message even though the problem was not entirely because of that and that behavior was one of the windows behavior for security purposes.
---
### Lab Environment and Virtual Machines Configurations
#### Lab Environment Behavior
- Virtual machine environments may behave differently from physical systems. In this lab, VM console sessions were processed similarly to remote sessions, which affected authentication requirements and troubleshooting outcomes.

#### Importance of static IP configuration for Domain Controllers
- Domain Controllers require a static IP address to maintain consistent DNS resolution and domain communication. Because Active Directory depends heavily on DNS, changing IP addresses would disrupt domain services, authentication, and client connectivity.


⬅️ [Previous: Testing and Troubleshooting](07-testing-and-troubleshooting.md) | [Next: Project Validation➡️](09-project-validation.md)
