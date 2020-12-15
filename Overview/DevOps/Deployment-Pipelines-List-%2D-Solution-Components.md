
|  Pipeline| Overview  | Remarks|
|--|--|--|
| [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) |Update Secrets in Key Vault (kv-cpd-apps-<env>-we-01) |
|[CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406)| Update App Configurations in the config store (acst-cpd-apps-<env>-we-01) and restart the pods| Run the key vault pipeline first if key vault references are added |
|[CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)| Deploy Platform APIs to AKS (aks-cpd-apps-<env>-we-01)|
|[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)| Deploy Web Apps to AKS (aks-cpd-apps-<env>-we-01)|
|[CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301)|Deploy integration function apps|


