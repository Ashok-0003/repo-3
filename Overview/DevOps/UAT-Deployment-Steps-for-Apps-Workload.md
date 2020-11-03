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
1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
Virtual Network
1. [rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
Route Tables
1. [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
Application Insights
Automation Account
Event Hub
Log Analytics
Storage Account
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
Application Insights
Automation Account
Event Hub
Log Analytics
Storage Account
1. [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
Network Security Groups
Key Vault

# Deployment of Apps Infrastructure
1. [rg-cpd-shrd-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=500)
APIM - apim-cpd-shrd-uat-we-01
Application Gateway - agw-cpd-shrd-uat-we-01
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
App Service - app-cpd-apps-qna-uat-we-01
App Service Plan - plan-cpd-apps-cog-we-01
Bot Service - bot-cpd-apps-cog-uat-we-01
Cognitive Service Luis Authoring - cog-cpd-apps-luisath-uat-we-01
Cognitive Service Luis Runtime - cog-cpd-apps-luisrt-uat-we-01
Cognitive Service QnAMaker - cog-cpd-apps-qna-uat-we-01 
Logic App -	logic-cpd-apps-cogsrch-we-01
Search Service - srch-cpd-apps-cog-uat-we-01
Web App Bot - app-cpd-apps-cog-uat-we-01
1. [rg-cpd-apps-int-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=498)
API Connection - apicon-cpd-apps-into365-uat-we-01
API Connection - apicon-cpd-apps-intsb-uat-we-01
API Connection - apicon-cpd-apps-intspo-uat-we-01
App Service Plan - plan-cpd-apps-int-uat-we-01
Event Hub - ev-cpd-apps-int-uat-we-01
Function App - func-cpd-apps-intbpa-uat-we-01
Logic App - logic-cpd-apps-intbpa-uat-we-01
Logic App - logic-cpd-apps-intcms-uat-we-01
Service Bus - sb-cpd-apps-int-uat-we-01
1. [rg-cpd-apps-aks-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=496)
AKS Cluster - aks-cpd-apps-uat-we-01
Application Gateway - agw-cpd-apps-aks-uat-we-01

# Deployment of the solution components
CD-<RepoName>-Release
<Work in progress>
