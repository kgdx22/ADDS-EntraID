# Automating Active Directory User Provisioning and Hybrid Identity Synchronization with Microsoft Entra ID

This lab demonstrates the implementation of a hybrid identity environment by integrating an on-premises Active Directory Domain Services (AD DS) environment with Microsoft Entra ID using Microsoft Entra Connect.

The project focuses on:

- Bulk user provisioning with PowerShell

- Organizational Unit (OU) management

- User Principal Name (UPN) standardization

- Directory synchronization with Microsoft Entra Connect

- Verification of cloud identities in Microsoft Entra ID


# 1. Bulk User Provisioning from CSV<br><br>
<img width="1919" height="1199" alt="ADDS" src="https://github.com/user-attachments/assets/cee69c0e-981b-4014-bbf0-f9295463fb3f" /><br><br>
A CSV file containing user attributes was imported using PowerShell and piped into the New-ADUser cmdlet. This automated the creation of multiple user accounts simultaneously and demonstrates how enterprise administrators efficiently onboard large groups of users. <br><br>
# 2. Create Organizational Unit<br><br>
<img width="1919" height="1199" alt="ADDC2" src="https://github.com/user-attachments/assets/0eb549c5-53f0-458e-be0a-a8b179ad891f" /><br><br>
A new OU named ConnectSyncUsers was created within Active Directory. Organizational Units provide administrative structure and this will be used to organize users, delegate permissions, and scope synchronization activities<br><br>
# 3. Move Existing Users into the target OU<br><br>
<img width="1919" height="1199" alt="ADDC6" src="https://github.com/user-attachments/assets/57061062-f229-410b-ae89-449ccdae3f33" /><br><br>
PowerShell was used to move user objects into the ConnectSyncUsers OU. This ensures that only intended identities are included within the synchronization scope configured later in Entra Connect.<br><br>
# 4. Update User Principal Names<br><br>
<img width="1919" height="1199" alt="ADDC4" src="https://github.com/user-attachments/assets/c0ca48ca-2514-44ef-9f3f-db5afcf5e2e3" /><br><br>
The target OU was stored as a PowerShell variable and Set-ADUser was used to update each user's UPN suffix to:<br><br>

*@udemytrials1001yahoo.onmicrosoft.com*<br><br>

This step ensures consistent authentication identities between Active Directory and Microsoft Entra ID.<br><br>
# 5. Configure Microsoft Entra Connect<br><br>
<img width="1919" height="1199" alt="ADDC3" src="https://github.com/user-attachments/assets/85c8fb65-b93d-4244-b13b-7d0f15bd189a" /><br><br>
Microsoft Entra Connect was launched and configured to communicate with the on-premises Active Directory forest. This allows user objects and attributes to be synchronized into Microsoft Entra ID.<br><br>
# 6. Configure OU Filtering<br><br>
<img width="1919" height="1199" alt="ADDC5" src="https://github.com/user-attachments/assets/69316060-c42c-44f7-be50-f273122be07f" /><br><br>
OU filtering was configured so that only the ConnectSyncUsers OU would synchronize to Microsoft Entra ID. This reflects a common enterprise practice used to maintain synchronization control and reduce unnecessary cloud objects.<br><br>
# 7. Verify Initial Synchronization
<img width="1919" height="1199" alt="ADDC7" src="https://github.com/user-attachments/assets/a6202a28-055b-41be-9c2b-1546fad3914e" /><br><br>
The Microsoft Entra admin center was reviewed to confirm that the Active Directory users successfully appeared within the tenant after synchronization completed.<br><br>
# 8. Refine User Provisioning Workflow
<img width="1919" height="1199" alt="ADDS8" src="https://github.com/user-attachments/assets/b1df89f9-b7c6-40b9-82c0-97b556159206" /><br><br>
A second batch of users was imported using a more streamlined PowerShell workflow that places users directly into the synchronization OU, reducing administrative overhead and improving consistency.<br><br>
# 9. Validate User Attributes<br><br>
<img width="1919" height="1199" alt="ADDC9" src="https://github.com/user-attachments/assets/a7eb9641-8bef-4a87-ad98-140471a88fa7" /><br><br>
The user account was reviewed in Active Directory Users and Computers to verify the UPN configuration and ensure it matched the Microsoft Entra tenant naming convention.<br><br>
# 10. Verify Additional Synchronization Results<br><br>
<img width="1919" height="1199" alt="ADDC10" src="https://github.com/user-attachments/assets/b59a9f5a-dd7c-495a-b6dc-41840d8ae707" /><br><br>
The Microsoft Entra admin center was reviewed again to verify that the second set of users successfully synchronized to the cloud tenant.<br><br>
# 11. Audit Users within the Synchronization OU
<img width="1919" height="1199" alt="ADDC11" src="https://github.com/user-attachments/assets/a24751d7-f410-4595-8506-5923c9b49bdb" /><br><br>
PowerShell was used to enumerate all users within the ConnectSyncUsers OU, providing a quick audit of the synchronized user population.<br><br><br><br>
## Outcome

This lab successfully demonstrates:

Hybrid Identity Architecture
Active Directory Administration
Microsoft Entra ID Integration
PowerShell Automation
User Lifecycle Management
Directory Synchronization
Identity Governance Fundamentals

The completed environment simulates how enterprise organizations synchronize and manage identities across on-premises and cloud platforms while maintaining centralized identity administration.



