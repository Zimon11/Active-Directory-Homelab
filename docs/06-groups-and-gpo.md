⬅️ [Previous: Client Domain Join](05-client-domain-join.md) | [Next: Troubleshooting ➡️](07-troubleshooting.md)

# 🔐 Groups and Group Policy (AGDLP)

### Step 5: Creating groups and applying GPOs
![Screenshot](../screenshots/Creating-groups/CreateGroup1.png)
- Created another OU in domain named **Groups**.

![Screenshot](../screenshots/Creating-groups/CreateGroup2.png)
- Created a dedicated Groups OU to centrally manage all security groups separately from users and computers.
- Separated Global Groups (user membership) and Domain Local Groups (resource and policy access) following the AGDLP model.

![Screenshot](../screenshots/Creating-groups/CreateGroup3.png)
- Created department-based Global Security Groups that will contain users from each department.

![Screenshot](../screenshots/Creating-groups/CreateGroup4.png)
- This Global Security Group will contain all users belonging to the HR department.

![Screenshot](../screenshots/Creating-groups/CreateGroup5.png)
- This image shows all of the groups of the Department OU inside of the Global group OU.

![Screenshot](../screenshots/Creating-groups/CreateGroup6.png)
- This image shows the group of the Admin Groups inside of the Global group OU.

![Screenshot](../screenshots/Creating-groups/CreateGroup7.png)
- Created a new Group for the Domain local Groups.
- This Domain Local Security Group will be used to assign access to resources such as file shares and computer logon rights.

![Screenshot](../screenshots/Creating-groups/CreateGroup8.png)
- This image shows all of the groups of the Access Groups inside of the Domain local groups.
- These Domain Local Groups will contain Global Groups, following the AGDLP (Accounts → Global → Domain Local → Permissions) model.

![Screenshot](../screenshots/Creating-groups/CreateGroup9.png)
- This image shows the groups that inside of the Admin-Access.

### Step 5.1: Adding users inside of their corresponding groups
![Screenshot](../screenshots/AddingUsersToGroups/AddUsers1.png)
- This image shows the users that are assigned to their corresponding Global security groups.

![Screenshot](../screenshots/AddingUsersToGroups/AddUsers2.png)
- This image shows the Users that is assigned to their Global security groups.
- Note: I created another 3 users previously for the HR, Finance and Admin.

### Step 5.2: Nesting Global security groups in Domain Local Groups
![Screenshot](../screenshots/AddingUsersToGroups/NestedGroups1.png)
- Global group of each department is nested inside of the domain local group to access the specific feature that the domail local group has and these Domain Local groups will later be used in GPO assignments to grant specific permissions.

![Screenshot](../screenshots/AddingUsersToGroups/NestedGroups3.png)
- This image list the all of the members in each of the Domain local groups the Access Groups and Admin Groups.

### Step 5.3: Applying GPO
![Screenshot](../screenshots/Creating-GPO/CreateGPO2.png)
- In Group Policy Management, Created a new GPO object.

![Screenshot](../screenshots/Creating-GPO/CreateGPO3.png)
- Edited the GPO object and navigated into the Computer Configuration> Windows Settings> Security Settings> Local Policies> User Rights Management.
- The **Allow log on locally** policy was configured to explicitly define which security groups are permitted to log on to domain-joined computers.

![Screenshot](../screenshots/Creating-GPO/CreateGPO4.png)
- Added the Domain local group inside of the policy to complete the AGDLP model.

![Screenshot](../screenshots/Creating-GPO/CreateGPO5.png)
- In this image list the Group that are included in the policy(Local Logon), when configuring a policy like this it always need to include the administrators.

![Screenshot](../screenshots/Creating-GPO/CreateGPO6.png)
- In this image also list the Group that are included in the policy(RDP).

![Screenshot](../screenshots/Creating-GPO/LinkGPO1.png)
- Linked the GPO into the corresponding OU to apply the policy.

![Screenshot](../screenshots/Creating-GPO/LinkGPO2.png)
- This image shows the GPO that is linked in the **Computer** OU of the IT Department.

![Screenshot](../screenshots/Creating-GPO/UpdateGPO1.png)
- In the Client computer, Logged-in as a Domain Administrator to update the policy of the computer.

![Screenshot](../screenshots/Creating-GPO/UpdateGPO2.png)
- In this image I logged in as the Domain user and open CMD As administrator to check if the policy is already applied.


⬅️ [Previous: Client Domain Join](05-client-domain-join.md) | [Next: Troubleshooting ➡️](07-troubleshooting.md)
