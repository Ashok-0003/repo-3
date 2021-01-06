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

# Deployment of Azure Infrastructure
1. [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
Application Insights
Automation Account
Event Hub Namespaces
Log Analytics
Storage Account
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
Application Insights
Automation Account
Event Hub Namespaces
Log Analytics
Storage Account
1. [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
Network Security Groups
Key Vault
1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
Virtual Network
1. [rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
Route Tables

# Deployment of Apps Infrastructure
1. [rg-cpd-shrd-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=500)
APIM - apim-cpd-shrd-uat-we-01
CDN - cdn-cpd-shrd-uat-we-01
CDN Endpoint - uat-tasmu
Storage Account - stcpdshrduatwe01

1. [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
App Config Store - acst-cpd-apps-str-uat-we-01
Cosmos Account - cosmos-cpd-apps-str-uat-we-01
Notification Hub - ntf-cpd-apps-str-uat-we-01
Notification Hub Namespace - ntfns-cpd-apps-str-uat-we-01
Redis Cache - redis-cpd-apps-str-uat-we-01
Service Bus - sb-cpd-apps-strntf-uat-we-01
Storage Account - stcpdappsstruatwe01
1. [rg-cpd-apps-cog-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=497)
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
1. [rg-cpd-apps-int-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=498)
API Connection - apicon-cpd-apps-into365-uat-we-01
API Connection - apicon-cpd-apps-intsb-uat-we-01
API Connection - apicon-cpd-apps-intspo-uat-we-01
API Connection - apicon-cpd-apps-integ-uat-we-01
API Connection - apicon-cpd-apps-intkv-uat-we-01
API Connection - apicon-cpd-apps-integd-uat-we-01
API Connection - apicon-cpd-apps-intst-uat-we-01
API Connection - apicon-cpd-apps-intcog-uat-we-01
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
Service Bus - sb-cpd-apps-int-uat-we-01
Storage Account - stcpdappsintuatwe01
1. [rg-cpd-apps-aks-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=496)
AKS Cluster - aks-cpd-apps-uat-we-01
Application Gateway - agw-cpd-apps-aks-uat-we-01
1. [rg-cpd-apps-waf-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=621)
Application Gateway - agw-cpd-apps-api-uat-we-01
Application Gateway - agw-cpd-apps-web-uat-we-01


## Link AKS Cluster DNS Zone to CPH Subscription
1. A user account being used should have access to both the subscriptions 
1. Go to AKS node resource group (rg-cpd-apps-aksnode-uat-we-01)
1. Open the private DNS Zone
1. Go to virtual network links and add link as below

![image.png](/.attachments/image-313a362b-dc66-4d5c-989b-61b8579b90a5.png)

# Creation and set up of AD B2C Tenant
Refer the document uploaded on [Ooredoo Sharepoint](https://ooredooonline.sharepoint.com/:w:/s/TASMU-CentralPlatformPMO/EdIKRGu6E1VGnA-naCTSBXQBjgdtCiT9C6n5E9rehxUWmw?e=ZSX2Yf)

# Deployment of the solution components
1. Add the key vault secrets for uat following this [wiki link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?anchor=adding-secrets-and-certificates-to-key-vault)
Stage for uat must be added to pipeline and run the pipeline to populate key vault - [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) (Uses powershell commands to import)
1. Add application configurations for uat  - [wiki link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?anchor=adding-configurations-to-app-config-store)
Add stage for uat to the app configuration seeding pipeline - [CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406) (Uses powershell commands to import)
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