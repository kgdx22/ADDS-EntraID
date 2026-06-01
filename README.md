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

<img width="1919" height="1199" alt="ADDC3" src="https://github.com/user-attachments/assets/85c8fb65-b93d-4244-b13b-7d0f15bd189a" /><br><br>
<img width="1919" height="1199" alt="ADDC5" src="https://github.com/user-attachments/assets/69316060-c42c-44f7-be50-f273122be07f" /><br><br>
<img width="1919" height="1199" alt="ADDC7" src="https://github.com/user-attachments/assets/a6202a28-055b-41be-9c2b-1546fad3914e" /><br><br>
<img width="1919" height="1199" alt="ADDS8" src="https://github.com/user-attachments/assets/b1df89f9-b7c6-40b9-82c0-97b556159206" /><br><br>
<img width="1919" height="1199" alt="ADDC9" src="https://github.com/user-attachments/assets/a7eb9641-8bef-4a87-ad98-140471a88fa7" /><br><br>
<img width="1919" height="1199" alt="ADDC10" src="https://github.com/user-attachments/assets/b59a9f5a-dd7c-495a-b6dc-41840d8ae707" /><br><br>
<img width="1919" height="1199" alt="ADDC11" src="https://github.com/user-attachments/assets/a24751d7-f410-4595-8506-5923c9b49bdb" /><br><br>




