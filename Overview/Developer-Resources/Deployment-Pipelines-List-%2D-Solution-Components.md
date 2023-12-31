
|  Pipeline| Overview  | Remarks|
|--|--|--|
| [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) |Update Secrets in Key Vault<br> (`kv-<sub>-apps-<env>-we-01`) | Secrets must be present in respective variable groups|
|[CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406)| Update App Configurations in the config store<br> (`acst-<sub>-apps-str-<env>-we-01`) and<br> restart the pods| Run the key vault pipeline first if key vault references are added |
|[CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)| Deploy Platform APIs to AKS<br> (`aks-<sub>-apps-<env>-we-01`)|
|[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)| Deploy Web Apps to AKS<br> (`aks-<sub>-apps-<env>-we-01`)|
|[CI-APIMConfig-CentralPlatformCore-Master-Build](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1146)| Update the APIM templates and files to artifacts storage account| Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-sbx-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=571)| Deploy the latest changes to sbx APIM<br> (apim-cpd-shrd-sbx-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-dev-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=572)| Deploy the latest changes to dev APIM<br> (apim-cpd-shrd-dev-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-tst-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=573)| Deploy the latest changes to tst APIM<br> (apim-cpd-shrd-tst-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-tra-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=574)| Deploy the latest changes to tra APIM<br> (apim-cpd-shrd-tra-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-APIMConfig-uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=575)| Deploy the latest changes to uat APIM<br> (apim-cpd-shrd-uat-we-01)| Dependent on execution of CI-APIMConfig-Master-Build, <br> Pass the run time variable BuildQueueInit with ; separated values for the apis to update|
|[CD-BotLuisQnAInitialDeploy](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=542&_a=summary)| To be DEPLOYED ONLY ONCE on environment creation.<br> Deploy the LUIS and QnaMaker instances to environments | Refer this Wiki page for more details on this - [Chatbot LUIS and Qnamaker deployments](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=luis-qnamaker-deployments)
|[CD-Bot-Release-Master](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=293&_a=summary)| Deploy the latest changes to Bot api (`app-<sub>-apps-bot-<env>-we-01`), deploy latest changes to General LUIS, Deploy latest changes to Bot related Function apps (`func-<sub>-apps-luistra-<env>-we-01` & `func-<sub>-apps-qnasync-<env>-we-01`)| |




