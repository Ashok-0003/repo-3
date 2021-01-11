# Pre requisites
1. ARM Modules must be created
1. Resource Group specific deployment files must be stitched
(Refer [README.md](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FREADME.md&_a=preview) of infra repo for details)
![image.png](/.attachments/image-86e9559c-b9eb-4af6-a652-35a13fad1574.png)
1. Merge all the code to master branch.
1. Wait for CI pipelines to complete for the templates to be uploaded to the artifacts storage account
1. Networking and infra resources must be deployed first
1. Global resources next - already deployed for non production environment (rg-cpd-glob-npd-we-01)
1. Specific resource group components can be deployed next
1. Solution components can be deployed on the azure resources at the end

# Global Resources for a tenant
[rg-cpd-glob-npd-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=393)
1. Azure Container Registry - acrcpdglobnpdwe01
2. Azure AD B2C Tenant - tasmucpb2cnonprod.onmicrosoft.com
3. Send Grid Account 

# Creation and set up of AD B2C Tenant
Refer the document uploaded on [Ooredoo Sharepoint](https://ooredooonline.sharepoint.com/:w:/s/TASMU-CentralPlatformPMO/EdIKRGu6E1VGnA-naCTSBXQBjgdtCiT9C6n5E9rehxUWmw?e=ZSX2Yf)

# Deployment of Azure Infrastructure
1. [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
**Dependencies** - 
**Resources** -
Application Insights - appi-cpd-shrd-mon-uat-we-01
Automation Account - aut-cpd-shrd-mon-uat-we-01
Event Hub Namespaces - evhns-cpd-shrd-mon-uat-we-01
Log Analytics - log-cpd-shrd-mon-uat-we-01
Storage Account - stcpdshrddiaguatwe01

1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
**Dependencies** - 
**Resources** -
Application Insights - appi-cpd-apps-mon-uat-we-01
Automation Account - aut-cpd-apps-mon-uat-we-01
Event Hub Namespaces - evhns-cpd-apps-mon-uat-we-01
Log Analytics - log-cpd-apps-mon-uat-we-01
Storage Account - stcpdappsdiaguatwe01

1. [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
**Dependencies** - [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
**Resources** -
Network Security Groups - nsg-cpd-apps-aks-uat-we-01, nsg-cpd-apps-agw-uat-we-01, nsg-cpd-apps-agwweb-uat-we-01, nsg-cpd-apps-agwapi-uat-we-01, nsg-cpd-apps-agwntf-uat-we-01, nsg-cpd-apps-apim-uat-we-01, nsg-cpd-apps-bkend-uat-we-01, nsg-cpd-apps-testvms-uat-we-01
Key Vault - kv-cpd-apps-uat-we-01

1. [rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
**Dependencies** -
**Resources** -
Route Tables - route-cpd-apps-aks-uat-we-01, route-cpd-apps-apim-uat-we-01, route-cpd-apps-bkend-uat-we-01, route-cpd-apps-testvms-uat-we-01

1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
**Dependencies** - [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
[rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
**Resources** -
Virtual Network - vnet-cpd-pltf-uat-we-01


# Deployment of Apps Infrastructure
1. [rg-cpd-shrd-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=500)
**Dependencies** - [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
[rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
**Resources** -
APIM - apim-cpd-shrd-uat-we-01
CDN - cdn-cpd-shrd-uat-we-01
CDN Endpoint - uat-tasmu
Storage Account - stcpdshrduatwe01

1. [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
**Dependencies** - 
**Resources** -
App Config Store - acst-cpd-apps-str-uat-we-01
Cosmos Account - cosmos-cpd-apps-str-uat-we-01
Cosmos DB - sql-cosmos-cpd-apps-str-ntf-uat-we-01, sql-cosmos-cpd-apps-str-pt-uat-we-01, sql-cosmos-cpd-apps-str-bot-uat-we-01
Cosmos DB Container - sqlc-cosmos-cpd-apps-str-ntf-uat-we-01, sqlc-cosmos-cpd-apps-str-botfb-uat-we-01, sqlc-cosmos-cpd-apps-str-botrt-uat-we-01, sqlc-cosmos-cpd-apps-str-botst-uat-we-01, sqlc-cosmos-cpd-apps-str-pt-uat-we-01, 
Notification Hub - ntf-cpd-apps-str-uat-we-01
Notification Hub Namespace - ntfns-cpd-apps-str-uat-we-01
Redis Cache - redis-cpd-apps-str-uat-we-01
Service Bus - sb-cpd-apps-strntf-uat-we-01
Storage Account - stcpdappsstruatwe01
1. Seed the Key Vault Secrets required in the cognitive and integration pipelines in kv-cpd-apps-uat-we-01

| Resource Name |Secret Name  | Key Vault Name |
|--|--|--|

<to be updated>

4. [rg-cpd-apps-cog-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=497)
**Dependencies** - [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394) <br> [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
[rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
**Resources** -
App Service - appcog-cpd-apps-qna-uat-we-01
App Service - appcog-cpd-apps-arqna-uat-we-01
App Service Plan - plan-cpd-apps-cog-we-01
Bot Service - bot-cpd-apps-cog-uat-we-01
Cognitive Service Luis Authoring - cog-cpd-apps-luisath-uat-we-01
Cognitive Service Luis Runtime - cog-cpd-apps-luisrt-uat-we-01
Cognitive Service QnAMaker English - appcog-cpd-apps-qna-uat-we-01 
Cognitive Service QnAMaker Arabic - appcog-cpd-apps-arqna-uat-we-01
Logic App -	logic-cpd-apps-cogsrch-we-01
Search Service - srch-cpd-apps-cog-uat-we-01
Web App Bot - app-cpd-apps-cog-uat-we-01

5. [rg-cpd-apps-int-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=498)
**Dependencies** - [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394) <br>[rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499) 
**Resources** -
API Connection - apicon-cpd-apps-into365-uat-we-01 - API Connection to Office 365 Tenant (CMS)
API Connection - apicon-cpd-apps-intsb-uat-we-01
API Connection - apicon-cpd-apps-intspo-uat-we-01
API Connection - apicon-cpd-apps-integ-uat-we-01
API Connection - apicon-cpd-apps-intkv-uat-we-01
API Connection - apicon-cpd-apps-integd-uat-we-01
API Connection - apicon-cpd-apps-intst-uat-we-01
API Connection - apicon-cpd-apps-intcog-uat-we-01
API Connection - apicon-cpd-apps-ascalrt-uat-we-01
API Connection - apicon-cpd-apps-intcds-uat-we-01
API Connection - apicon-cpd-apps-prdcds-uat-we-01
App Service Plan - plan-cpd-apps-int-uat-we-01
Event Hub - ev-cpd-apps-int-uat-we-01
Event Grid Domain - egd-cpd-apps-int-uat-we-01
Function App - func-cpd-apps-intbpa-uat-we-01
Function App - func-cpd-apps-intntf-uat-we-01
Logic App - logic-cpd-apps-inttrsl-uat-we-01
Logic App - logic-cpd-apps-intaprv1-uat-we-01
Logic App - logic-cpd-apps-intgbaprl-uat-we-01
Logic App - logic-cpd-apps-intprdt-uat-we-01
Logic App - logic-cpd-apps-intsec-uat-we-01
Logic App - logic-cpd-apps-route-uat-we-01
Logic App - logic-cpd-apps-6dbill-uat-we-01
Logic App - logic-cpd-apps-6dhook-uat-we-01
Logic App - logic-cpd-apps-mpsidx-uat-we-01
Logic App - logic-cpd-apps-mpsd365-uat-we-01
Logic App - logic-cpd-apps-mpso365-uat-we-01
Logic App - logic-cpd-apps-dfndr-uat-we-01
Logic App - logic-cpd-apps-intfile-uat-we-01
Logic App - logic-cpd-apps-intsubs-uat-we-01
Service Bus - sb-cpd-apps-int-uat-we-01
Service Bus Queue - sbq-cpd-apps-intprodsync-uat-we-01, sbq-cpd-apps-intntf-uat-we-01, sbq-cpd-apps-intsec-uat-we-01, sbq-cpd-apps-int6dbill-uat-we-01, sbq-cpd-apps-intd365-uat-we-01, sbq-cpd-apps-into365-uat-we-01, sbq-cpd-apps-intchglog-uat-we-01, sbq-cpd-apps-intaprvl-uat-we-01, sbq-cpd-apps-intgbaprl-uat-we-01, sbq-cpd-apps-intcoreapi-uat-we-01, sbq-cpd-apps-intiotalert-uat-we-01
Service Bus Topic - sbt-cpd-apps-qnasync-uat-we-01
Service Bus Topic Subscription - sbts-cpd-apps-copyqna-uat-we-01
Storage Account - stcpdappsintuatwe01

6.  [rg-cpd-apps-aks-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=496)
**Dependencies** - [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
[rg-cpd-glob-npd-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=393)
[rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
[rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
**Resources** -
AKS Cluster - aks-cpd-apps-uat-we-01
Managed Identity - mi-cpd-apps-aks-uat-we-01 (Deployed in rg-cpd-apps-aksnode-uat-we-01)
Application Gateway - agw-cpd-apps-aks-uat-we-01


7. [rg-cpd-apps-waf-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=621)
**Dependencies** - [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
[rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
**Resources** -
Application Gateway - agw-cpd-apps-api-uat-we-01
Application Gateway - agw-cpd-apps-web-uat-we-01
Application Gateway - agw-cpd-apps-ntf-uat-we-01

8. Updating Key Vault Access Policies - kv-cpd-apps-uat-we-01

|Object Id| Secrets |  Certificates|
|--|--|--|
|mi-cpd-apps-aks-uat-we-01|Get||
|app-cpd-apps-bot-uat-we-01|Get||
|func-cpd-apps-qnasync-uat-we-01|Get||
|func-cpd-apps-luistra-uat-we-01|Get||
|func-cpd-apps-intbpa-uat-we-01|Get|Get|

9. Seeding secrets to Key Vault (kv-cpd-apps-uat-we-01)
<To Be Updated> the list of secrets - Scripts\KeyVault\all-secrets.yml
Add the key vault secrets for the env following this [wiki link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?anchor=adding-secrets-and-certificates-to-key-vault)
Stage for uat must be added to pipeline and run the pipeline to populate key vault - [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) (Uses powershell commands to import)
10. Adding Configurations to App Config Store (acst-cpd-apps-str-uat-we-01)
<To Be Updated> the configurations and their retrieval - Scripts\AppConfigurations
Add application configurations for uat  - [wiki link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?anchor=adding-configurations-to-app-config-store)
Add stage for uat to the app configuration seeding pipeline - [CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406) (Uses powershell commands to import)

## Link AKS Cluster DNS Zone to CPH Subscription
1. A user account being used should have access to both the subscriptions 
1. Go to AKS node resource group (rg-cpd-apps-aksnode-uat-we-01)
1. Open the private DNS Zone
1. Go to virtual network links and add link as below

![image.png](/.attachments/image-313a362b-dc66-4d5c-989b-61b8579b90a5.png)
## Role Assignments 
1. CDN Endpoint Contributor
2. App Configuration Store Data Reader
3. AKS indentities
<to be updated>
## Configuring Notification Hubs for APN and Firebase

# Deployment of the solution components
1. Add the CI and CD APIM Pipelines and URLs pointing to AKS AGW for most of the APIs
![image.png](/.attachments/image-9b9f0d1d-d858-4764-aa2a-a2f6e477f0cd.png)
1. For platform apis, ingress controller helm-config needs to be added for new env (refer above image) and stage should be added to [CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141) pointing to the new env
1. For integration function apps, add stage to the following pipeline pointing to uat resources
[CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301)
1. For web apps, add stage to the following pipeline pointing to uat resources
[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)

1. [Deploying Chatbot solutions](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=webapp-bot-ad-update)

1. For deploying Payment Preference function to function app, add stage to the following pipeline 
[CD-PlatformFuncApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=738)