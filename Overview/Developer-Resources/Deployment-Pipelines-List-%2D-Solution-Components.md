
|  Pipeline| Overview  | Remarks|
|--|--|--|
| [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) |Update Secrets in Key Vault (kv-cpd-apps-<env>-we-01) |
|[CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406)| Update App Configurations in the config store (acst-cpd-apps-<env>-we-01) and restart the pods| Run the key vault pipeline first if key vault references are added |
|[CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)| Deploy Platform APIs to AKS (aks-cpd-apps-<env>-we-01)|
|[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)| Deploy Web Apps to AKS (aks-cpd-apps-<env>-we-01)|
|[CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301)|Deploy integration function apps|
|[CI-APIMConfig-Master-Build](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=570)| Update the APIM templates and files to artifacts storage account| Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-sbx-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=571)| Deploy the latest changes to sbx APIM (apim-cpd-shared-sbx-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-dev-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=572)| Deploy the latest changes to dev APIM (apim-cpd-shared-dev-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-tst-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=573)| Deploy the latest changes to tst APIM (apim-cpd-shared-tst-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-tra-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=574)| Deploy the latest changes to tra APIM (apim-cpd-shared-tra-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=575)| Deploy the latest changes to uat APIM (apim-cpd-shrd-uat-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293&_a=summary)| Deploy the latest changes to Bot api (app-cpd-apps-bot-<env>-we-01), deploy latest changes to General LUIS, Deploy latest changes to Bot related Function apps (func-cpd-apps-luistra-<env>-we-01 & func-cpd-apps-qnasync-<env>-we-01)| |
|[CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary)| To be DEPLOYED ONLY ONCE On environment creation. Deploy the LUIS and QnaMaker instances to environments ||





