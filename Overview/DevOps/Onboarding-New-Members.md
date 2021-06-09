[[_TOC_]]

# Fill RBAC Excel
1. Fill the resource information in [TASMU RBAC](https://microsofteur.sharepoint.com/:x:/t/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/ESoPzSk_bHVHktzXLI8XSZgB7ER7ZBT73CbyiIlkSKwyEA?e=dplOpa)
1. Get the member account created in Azure AD by Fahim Mohammed Mathany (fmathany@malomatia.com) or any Malomatia POC for this activity.
# Add the account to ADO team
- [TASMU MS Apps Workstream](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTE1MDYzNjEzOC0zMTQ0ODEyODc2LTI2MDA2NjM0NzItMTI4MTY3MTQ1OQ)
- [TASMU MS Biz Apps Workstream](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTEwNjE1MzUxNjgtNzQyMjY5NzcxLTI3MDIyMTg0NTktMzQwNjk0MjA4Mg)
- [TASMU MS DAI Workstream](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTE1Mjk1OTE0NzYtMjIxMjIxNDg2My0zMDgwOTczNTIwLTk3OTg1NDE3Mw)
- [TASMU MS MW Workstream](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTMwNDU3NDQ4NTYtMjE3MTI3NzYzMi0yNjgwNzYxNTIyLTM4NjM2NjgxOA)
- [TASMU MS SI Workstream](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTEwOTMzMTI0NTItNDEzNjU2NDU1MC0yNTgxMDEzODcwLTc2NTk3NjM5Ng)
- [TASMU MS CCOE](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTIyMDM1NTIxNDItMjQ3ODgyNjU2NS0yNDU4MTM5Njk3LTEzOTk1MTExOQ)
- [TASMU MS Architects](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTEzMDk3Mjc4OTItNDI5MzYyOTI1My0yNDcyMTc2ODIwLTIzODA2MTk2MzM)
- [TASMU MS SQA TQA](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/teams?subjectDescriptor=vssgp.Uy0xLTktMTU1MTM3NDI0NS04NjY3NTY2NC0yMjk4MzkzNjc4LTMxMzI0MDY0OTAtNDIzMzY4NjAxMC0xLTQxMTYxODAxOTItNDY2ODcxNjMxLTI4MjQ3NDQzMTktMTA3Nzg1ODg2MQ)

# Update User Access (if required):
1. Add a new record in [RBAC Sheet](https://microsofteur.sharepoint.com/:x:/t/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/ESoPzSk_bHVHktzXLI8XSZgB7ER7ZBT73CbyiIlkSKwyEA?e=dplOpa)
1. For Azure resources RBAC/PIM, send an email to Fahim Mohammed Mathany (fmathany@malomatia.com) or any Malomatia POC for this activity to change the permission as per the RBAC sheet.
1. For DevOps, If user needs access to advanced features in DevOps like repositories update the access to Basic.
1. More about different access levels - [refer](https://docs.microsoft.com/en-us/azure/devops/organizations/security/access-levels?view=azure-devops)

# Subscription Access
1. Add a new record in [RBAC Sheet](https://microsofteur.sharepoint.com/:x:/t/TASMUNationalPlatform-DeliveryStream-MicrosoftOnly/ESoPzSk_bHVHktzXLI8XSZgB7ER7ZBT73CbyiIlkSKwyEA?e=dplOpa)
1. For Azure resources RBAC/PIM, send an email to Fahim Mohammed Mathany (fmathany@malomatia.com) or any Malomatia POC for this activity to change the permission as per the RBAC sheet.

1. Refer [Microsoft RBAC](/Overview/DevOps/Microsoft-RBAC) wiki for details on different groups
1. PIM should be used all the time for the provided access. Permissions should be granted on granular level. Avoid providing access to whole subscription unless absolutely required. 
1. Coordinate with Fahim or any Malomatia POC for revoking the access or removing the account when it is not required. Please refer to [Account Deletion Process](/Overview/DevOps/Removing-Users) for more details.