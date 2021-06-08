[[_TOC_]]
# Notes
1. UAT release can be picked only after it has been deployed on test environment successfuly
1. For each of the below deployments, pick the ones in which tst stage has succeeded and uat is waiting for approval
1. For a step, if the latest tst env run is already deployed to uat, an update is not required on uat, proceed to next step.
![image.png](/.attachments/image-7770911c-bb27-472a-ab75-ca1ebe423177.png)
1. Approval can be made by clicking on the 0/1 checks passed
![image.png](/.attachments/image-9e510c68-d835-402e-ade2-4ae6be0b2806.png)

# 1. Update Key Vault
[CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337)
# 2. Update App Configurations
[CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406)
# 3. Deploy Platform APIs and Function Apps
[CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)
# 4. Deploy CDN Container
[CD-CDNContainer-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=967)
# 5. Deploy Web Apps or Portals
[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)

# 6. Deploy Bot 
[CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293)
# 7. Deploy CRM
[CD-CrmPlatform-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=111)
# 8. Build and Release Mobile Apps
[CI-MobileApps-Android-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=36)
[CI-MobileApps-iOS-Build](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=108)
