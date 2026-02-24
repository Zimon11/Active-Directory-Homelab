⬅️ [Previous: Lessons Learned](08-lessons-learned.md)
# 📚 Additional and Validation
### Disabling Control Panel with Security Filtering
![Screenshot](../screenshots/Extra/DisableControlPanel1.png)
- Added a new IT user

![Screenshot](../screenshots/Extra/DisableControlPanel2.png)
- Make another Group that will contain the IT user contractor.
- Note there's two different role in IT users the Employee and the contractor.

![Screenshot](../screenshots/Extra/DisableControlPanel3.png)
- Added and configured a new GPO that will restrict the Control panel of the IT Contractors.
- This is a user configuration, navigated to User Configuration>Administrative Templates>Control Panel> then enable the Prohibit the access to Control panel and settings and link the GPO into the IT users OU.

![Screenshot](../screenshots/Extra/DisableControlPanel4.png)
- Remove the Authenticated Users from the security filtering to specify the user or group that will use the GPO.

![Screenshot](../screenshots/Extra/DisableControlPanel5.png)
- Add the group that will use the Disable Control Panel GPO which is the GG_IT_Contractor.

![Screenshot](../screenshots/Extra/DisableControlPanel6.png)
- Navigated into the delagation tab and add the Authenticated users, make sure that the permission is in the read only and the apply gpo is also disabled for other users that is not included in the group to still be able to access the control panel.

![Screenshot](../screenshots/Extra/DisableControlPanel7.png)
- Verified the permission of the Authenticated Users.

![Screenshot](../screenshots/Extra/DisableControlPanel8.png)
- Added the same Group into the IT GPO logon rights for the group to be able to logged in into the workstation.
- Note they have the same workstation but the IT contractor group has more restrictions.

![Screenshot](../screenshots/Extra/DisableControlPanel9.png)
- Logged-in using the IT contractor's account and open CMD as administrator to apply the policy.

![Screenshot](../screenshots/Extra/DisableControlPanel10.png)
- Verified that the policy is already updated.

### Validation
![Screenshot](../screenshots/Extra/Validation1.png)
- In the IT workstation, Logged-in as the IT Contractor and verified that the GPO is working.

![Screenshot](../screenshots/Extra/Validation2.png)
- In the IT workstation, Logged-in as the IT Employee and verified that the GPO security filtering is working properly and the control panel of this group is still working.

### Password Reset
![Screenshot](../screenshots/Extra/PasswordReset1.png)
- Search the user that will reset the password.

![Screenshot](../screenshots/Extra/PasswordReset2.png)
- Click the Reset password in the options.

![Screenshot](../screenshots/Extra/PasswordReset3.png)
- Use a strong password for the user.

![Screenshot](../screenshots/Extra/PasswordReset4.png)
- The user password was successfully changed.

### RBAC Validation
#### Validation in the HR workstation
![Screenshot](../screenshots/Extra/Validation4.png)
- Logged-in in the HR workstation using the IT user credentials.

![Screenshot](../screenshots/Extra/Validation5.png)
- The logged-in failed due to the restriction of the GPO that is added in the HR workstation.
- Only HR user will be able to logged-in in the HR workstation.

#### Validation in the IT workstation
![Screenshot](../screenshots/Extra/Validation6.png)
- Logged-in in the IT workstation using the HR user credentials.

![Screenshot](../screenshots/Extra/Validation7.png)
- The logged-in failed and also show the same error in the HR workstation thats because of the restriction that has been added into the GPO IT workstation.
- Only IT users will be able to logged-in in the IT workstation.
⬅️ [Previous: Lessons Learned](08-lessons-learned.md)