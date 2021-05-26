[[_TOC_]]
# 1. Prerequisites
1. [Self Hosted Agents](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/159/Self-Hosted-Agents) equivalent to Microsoft Hosted Windows Agent provisioned in Central Platform Hub VNet to deploy APIM and AKS solutions
1. ARM Modules must be created
1. Resource Group specific deployment files must be stitched
(Refer [README.md](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FREADME.md&_a=preview) of infra repo for details)
![image.png](/.attachments/image-86e9559c-b9eb-4af6-a652-35a13fad1574.png)
1. Merge all the code to master branch.
1. Wait for CI pipelines to complete for the templates to be uploaded to the artifacts storage account
1. Networking and infra resources must be deployed first
1. Global resources next - already deployed for non production environment (`rg-<sub>-glob-npd-we-01`)
1. Specific resource group components can be deployed next
1. Solution components can be deployed on the azure resources at the end

# 2. Global Resources for a tenant
## 2.1 Global Non Production Resource Group
### 2.1.1 Resource Group
`rg-<sub>-glob-npd-we-01`
### 2.1.2 Dependencies
### 2.1.3 Resources
Azure AD B2C Tenant - tasmucpb2cnonprod.onmicrosoft.com 
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ContainerRegistry | `acr<sub>globnpdwe01` | |
|SendGrid | `sga-<sub>-glob-email-npd-we-01` | Silver Tier |

## 2.2 Global Consumption Metering Resource Group
### 2.2.1 Resource Group
`rg-<sub>-glob-acm-we-01`
### 2.2.2 Dependencies
### 2.2.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|StorageAccount | `st<sub>globacmwe01` ||
- [Create a daily export of azure consumption metering for 6D Billing](https://docs.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-export-acm-data?tabs=azure-portal#create-a-daily-export)

![image.png](/.attachments/image-e4ddd176-01e7-404c-80f1-9a337e259737.png)

## 2.3 Creation and set up of AD B2C Tenant
Refer the document uploaded on [Ooredoo Sharepoint](https://ooredooonline.sharepoint.com/:w:/s/TASMU-CentralPlatformPMO/EdIKRGu6E1VGnA-naCTSBXQBjgdtCiT9C6n5E9rehxUWmw?e=ZSX2Yf)

## 2.4 Register the applications in AD and AD B2C
1. [AD B2C Registrations](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad-b2c)
2. [AAD Registrations](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad---tasmusqcp.onmicrosoft.com)

# 3. Deployment of networking and monitoring infrastructure
## 3.1 Shared Monitoring Resource Group
### 3.1.1 Resource Group
`rg-<sub>-shrd-mon-<env>-we-01`
### 3.1.2 Dependencies
### 3.1.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApplicationInsights | `appi-<sub>-shrd-mon-<env>-we-01`||
|AutomationAccounts | `aut-<sub>-shrd-mon-<env>-we-01`||
|EventHubNamespaces | `evhns-<sub>-shrd-mon-<env>-we-01`||
|LogAnalytics | `log-<sub>-shrd-mon-<env>-we-01`||
|StorageAccount | `st<sub>shrddiag<env>we01`||

## 3.2 Apps Monitoring Resource Group
### 3.2.1 Resource Group
`rg-<sub>-apps-mon-<env>-we-01`
### 3.2.2 Dependencies
### 3.2.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ActionGroup | `ag-<sub>-apps-mon-<env>-we-01`||
|ApplicationInsights | `appi-<sub>-apps-mon-<env>-we-01`||
|AutomationAccounts | `aut-<sub>-apps-mon-<env>-we-01`||
|EventHubNamespaces | `evhns-<sub>-apps-mon-<env>-we-01`||
|LogAnalytics | `log-<sub>-apps-mon-<env>-we-01`||
|StorageAccount | `st<sub>appsdiag<env>we01`||

## 3.3 Apps Security Resource Group
### 3.3.1 Resource Group
`rg-<sub>-apps-sec-<env>-we-01`
### 3.3.2 Dependencies
1. `rg-<sub>-apps-mon-<env>-we-01`
### 3.3.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|NetworkSecurityGroups | `nsg-<sub>-apps-aks-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-agw-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-agwweb-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-agwapi-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-agwntf-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-apim-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-bkend-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-testvms-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-ckndflt-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-cknagw-<env>-we-01`||
|NetworkSecurityGroups | `nsg-<sub>-apps-cknredis-<env>-we-01`||
|KeyVault | `kv-<sub>-apps-<env>-we-01` | Access Policy added only for ADO Service Connection |

## 3.4 Apps Networking Resource Group
### 3.4.1 Resource Group
`rg-<sub>-apps-net-<env>-we-01`
### 3.4.2 Dependencies
### 3.4.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|RouteTables | `route-<sub>-apps-aks-<env>-we-01`||
|RouteTables | `route-<sub>-apps-apim-<env>-we-01`||
|RouteTables | `route-<sub>-apps-bkend-<env>-we-01`||
|RouteTables | `route-<sub>-apps-testvms-<env>-we-01`||
|RouteTables | `route-<sub>-apps-ckndflt-<env>-we-01`||
|PrivateEndpoint| `prvep-<sub>-apps-cosmos-<env>-we-01` |[Refer this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/119/UAT-Apps-Workload-Deployment-Steps?anchor=5.3-add-private-endpoints-to-resources)|
|PrivateEndpoint| `prvep-<sub>-apps-sbntf-<env>-we-01` |[Refer this](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/119/UAT-Apps-Workload-Deployment-Steps?anchor=5.3-add-private-endpoints-to-resources)|

## 3.5 Platform Networking Resource Group
### 3.5.1 Resource Group
`rg-<sub>-pltf-net-<env>-we-01`

### 3.5.2 Dependencies
1. `rg-<sub>-apps-sec-<env>-we-01`
1. `rg-<sub>-apps-net-<env>-we-01`
### 3.5.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|VirtualNetwork | `vnet-<sub>-pltf-<env>-we-01`||
|PrivateDNSZones| `<sub>-privatelink.cosmos.windows.net` ||
|PrivateDNSZones| `<sub>-privatelink.servicebus.windows.net` ||
|PrivateDNSZones| `<sub>-privatelink.westeurope.azmk8s.io`||

1. One DNS Zone can have multiple virtual networks hence only one DNS Zone is required for a resource on a subscription. [Refer rg-cpd-pltf-net-dev-we-01 from dev subscription](https://portal.azure.com/#@tasmusqcp.onmicrosoft.com/resource/subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-pltf-net-dev-we-01/providers/Microsoft.Network/privateDnsZones/privatelink.cosmos.windows.net/overview).

1. Deploy `rg-<sub>-pltf-net-<env>-we-01`


## 3.6 Platform Security Resource Group
### 3.6.1 Resource Group
`rg-<sub>-pltf-sec-<env>-we-01`
### 3.6.2 Dependencies
### 3.6.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|KeyVault |`kv-<sub>-pltf-<env>-we-01` |Access Policy added only for ADO Service Connection|
|ManagedIdentity |`mi-<sub>-pltf-<env>-we-01` ||

## 3.7 Update Key Vault Access Policies
 `kv-<sub>-pltf-<env>-we-01`
 redeploy `rg-<sub>-pltf-sec-<env>-we-01`

|Object Id| Secrets |  Certificates|
|--|--|--|
|`mi-<sub>-pltf-<env>-we-01`|Get|Get|


# 4. Deployment of Apps Infrastructure
## 4.1 Apps Storage Resource Group
### 4.1.1 Resource Group
`rg-<sub>-apps-str-<env>-we-01`
### 4.1.2 Dependencies
### 4.1.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|AppConfigurationStore|`acst-<sub>-apps-str-<env>-we-01`||
|CosmosAccount | `cosmos-<sub>-apps-str-<env>-we-01`||
|CosmosDBSQL |`sql-cosmos-<sub>-apps-str-ntf-<env>-we-01`||
|CosmosDBSQL| `sql-cosmos-<sub>-apps-str-pt-<env>-we-01` ||
|CosmosDBSQL| `sql-cosmos-<sub>-apps-str-bot-<env>-we-01`||
|CosmosDBSQLContainer | `sqlc-cosmos-<sub>-apps-str-ntf-<env>-we-01`||
|CosmosDBSQLContainer | `sqlc-cosmos-<sub>-apps-str-botfb-<env>-we-01`||
|CosmosDBSQLContainer | `sqlc-cosmos-<sub>-apps-str-botrt-<env>-we-01`||
|CosmosDBSQLContainer | `sqlc-cosmos-<sub>-apps-str-botst-<env>-we-01`||
|CosmosDBSQLContainer | `sqlc-cosmos-<sub>-apps-str-pt-<env>-we-01`||
|NotificationHub | `ntf-<sub>-apps-str-<env>-we-01`||
|NotificationHubNamespace | `ntfns-<sub>-apps-str-<env>-we-01`||
|RedisCache | `redis-<sub>-apps-str-<env>-we-01`| Use 2020-06-01 Module for deploying Azure Cache for Redis instance with Availability zones. |
|ServiceBusNamespace| `sb-<sub>-apps-strntf-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strntfbulk-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strntfbulkdl-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strntfoutboundgsmssingle-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strntfsingle-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strsmsbulk-<env>-we-01`||
|ServiceBusNamespaceTopic| `sbt-<sub>-apps-strsmssingle-<env>-we-01`||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strntfbulk-<env>-we-01` ||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strntfbulkdl-<env>-we-01`||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strntfoutboundgsmssingle-<env>-we-01`||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strntfsingle-<env>-we-01`||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strsmsbulk-<env>-we-01`||
|ServiceBusNamespaceTopicSubscription | `sbts-<sub>-apps-strsmssingle-<env>-we-01`||
|StorageAccount | `st<sub>appsstr<env>we01`||
|StorageAccount | `st<sub>appsapimt<env>we01`|

## 4.2 Seed the Key Vault Secrets in 
`kv-<sub>-apps-<env>-we-01`
required in the cognitive and integration pipelines 

| Resource Name |Secret Name  | Key Vault Name | Usage|
|--|--|--|--|
|`apicon-<sub>-apps-intcds-<env>-we-01`|Crm-CaseManagement-DynamicsSettings-ClientSecret|`kv-<sub>-apps-<env>-we-01`| Client Secret of the [App Registration (spn-crm-case-management-integration-<env>)](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments) - to authenticate Common Data Service Connection|
|`apicon-<sub>-apps-prdcds-<env>-we-01`|Crm-Common-DynamicsSettings-ClientSecret|`kv-<sub>-apps-<env>-we-01`| Client Secret of the [App Registration (spn-crm-common-integration-<env>)](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments) - to authenticate Common Data Service Connection|
|`apicon-<sub>-apps-pflcds-<env>-we-01`|Crm-ProfileManagement-DynamicsSettings-ClientSecret|`kv-<sub>-apps-<env>-we-01`| Client Secret of the [App Registration (spn-crm-common-integration-<env>)](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments) - to authenticate Common Data Service Connection|
|`apicon-<sub>-apps-integ-<env>-we-01`, `apicon-<sub>-apps-ckankv-<env>-we-01`|sqcp-ado-spn-client-id|`kv-<sub>-pltf-<env>-we-01`| Client Id of the service principal having contributor access on integration event grid domain  to authenticate event grid api connection
|`apicon-<sub>-apps-integ-<env>-we-01`,`apicon-<sub>-apps-ckankv-<env>-we-01`|sqcp-ado-spn-client-secret|`kv-<sub>-pltf-<env>-we-01`| Client Secret of the service principal having contributor access on integration event grid domain to authenticate event grid api connection|
|`logic-<sub>-apps-apimt-<env>-we-01`|ARMAPI-ClientSecret|`kv-<sub>-apps-<env>-we-01`| Client Secret of the service principal with Reader access on APIM to allow it to query APIM metering data|

## 4.3 Apps Cognitive Resource Group
### 4.3.1 Resource Group
`rg-<sub>-apps-cog-<env>-we-01`
### 4.3.2 Dependencies
1. `rg-<sub>-apps-mon-<env>-we-01`
1. `rg-<sub>-apps-str-<env>-we-01`
1. `rg-<sub>-apps-sec-<env>-we-01`
1. App Registration - `spn-bot-<env>`
1. Enable West US location policy for deployment of QnA Maker:
    It can be enabled specifically for following resource groups:	
        - `rg-<sub>-apps-cog-<env>-we-01`
        - `rg-cph-pltf-iacstg-prd-we-01`
        - `rg-cph-pltf-iacst-prd-we-01`

### 4.3.3 Notes
4.3.3.1. Naming Convention 
Naming convention has deviation because QnA Maker requires names for both App Service and Cognitive Service as identical. It was consulted with product team and it's an issue in QnA Maker. This is the reason why app service and cognitive service for QnaMaker are named as `appcog-<sub>-apps-qna-<env>-we-01` for English and `appcog-<sub>-apps-arqna-<env>-we-01` for Arabic.

4.3.3.2. Location
 QnA resources -  `app-<sub>-apps-qna-<env>-we-01` and `app-<sub>-apps-arqna-<env>-we-01` are deployed in West US as that is the only supported location for resource type - QnA. 
More Information on this limiation - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra/pullrequest/3568)

### 4.3.4 Resources -
| Module Name | Parameter File Name | Remarks |
|--|--|--|
| AppServiceManagement | `app-<sub>-apps-qna-<env>-we-01` | App service for English QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePropertiesQnA | `app-<sub>-apps-qna-<env>-we-01` | App service for English QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePlanScale | `scale-<sub>-apps-cog-<env>-we-01` | App service scale for Bot api App Service
| AppServiceManagement | `app-<sub>-apps-arqna-<env>-we-01`| App service for Arabic QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePropertiesQnA | `app-<sub>-apps-arqna-<env>-we-01` | App service for Arabic QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServiceManagement | `app-<sub>-apps-bot-<env>-we-01` | App service for Bot API
|AppServicePlan | `plan-<sub>-apps-cog-<env>-we-01`
| CognitiveServices | `cog-<sub>-apps-luisauth-<env>-we-01` | Luis Authoring
| CognitiveServices | `cog-<sub>-apps-luisrt-<env>-we-01` | Luis Runtime
| CognitiveServicesQna | `cog-<sub>-apps-qna-<env>-we-01` | QnAMaker English - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
|CognitiveServicesQna | `cog-<sub>-apps-arqna-<env>-we-01`| QnAMaker Arabic - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2F<env>%20Environment%20Provisioning%20Guide%2F<env>%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
|FunctionAppQna | `func-<sub>-apps-luistra-<env>-we-01` | func app luis trainer
|FunctionAppQna | `func-<sub>-apps-qnasync-<env>-we-01` | func app triggered by `logic-<sub>-apps-qnakbsync-<env>-we-01`
|SearchService | `srch-<sub>-apps-cog-<env>-we-01` | Search Service English Cognitive Service for QnAMaker
|SearchService | `srch-<sub>-apps-arcog-<env>-we-01` | Search Service Arabic Cognitive service for QnAMaker
| WebappBot | `bot-<sub>-apps-<env>-we-01` | appId is ClientID of App Registration spn-bot-<env>

## 4.4 Apps Integration Resource Group 
### 4.4.1 Resource Group
`rg-<sub>-apps-int-<env>-we-01`

### 4.4.2 Dependencies
1. `rg-<sub>-apps-mon-<env>-we-01`
1. `rg-<sub>-apps-str-<env>-we-01`
1. `rg-<sub>-glob-acm-we-01`
1. Two secrets added to `kv-<sub>-pltf-<env>-we-01`
1. `rg-<sub>-pltf-sec-<env>-we-01`
1. App registration for `spn-armapi-reader-<env>` 
1. Seeding of ARMAPI-ClientSecret in the `kv-<sub>-apps-<env>-we-01` Key Vault
1. Seeding of CPCoreApis-ClientSecret in the `kv-<sub>-apps-<env>-we-01` Key Vault
1. If its a **fresh deployment** then change the value of "**deploy**" parameter to **true** in `apicon-<sub>-apps-intspo-<env>-we-01-parameters.json` and `apicon-<sub>-apps-into365-<env>-we-01-parameters.json`


### 4.4.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|APIConnection | `apicon-<sub>-apps-into365-<env>-we-01` | API Connection to Office 365 Tenant (CMS)|
|ApiConnectionServiceBus | `apicon-<sub>-apps-intsb-<env>-we-01` | API Connection to Service Bus|
|APIConnection | `apicon-<sub>-apps-intspo-<env>-we-01` | API Connection to Sharepoint Online|
|ApiConnectionEventGrid |`apicon-<sub>-apps-integ-<env>-we-01` | API Connection to Event Grid Domain|
|ApiConnectionKeyVault | `apicon-<sub>-apps-intkv-<env>-we-01` ||
|ApiConnectionEventGridPublish | `apicon-<sub>-apps-integd-<env>-we-01` | (Refer - `kv-<sub>-pltf-<env>-we-01` for secret)
|ApiConnectionAzureBlob | `apicon-<sub>-apps-apimtst-<env>-we-01`| API Connection to `st<sub>appsapimt<env>we01` in `rg-<sub>-apps-str-<env>-we-01`|
|ApiConnectionAzureBlob | `apicon-<sub>-apps-intst-<env>-we-01`||
|ApiConnectionAzureBlob | `apicon-<sub>-apps-strst-<env>-we-01`| API Connection to `st<sub>appsstr<env>we01` in `rg-<sub>-apps-str-<env>-we-01`|
|APIConnectionCognitiveService | `apicon-<sub>-apps-intcog-<env>-we-01` | API Connection to Translator Cognitive Service|
|APIConnection | `apicon-<sub>-apps-ascalrt-<env>-we-01` | API Connection to Azure Security Alert trigger.|
|ApiConnectionCommonDataService | `apicon-<sub>-apps-intcds-<env>-we-01` | API Connection to Common Data Service for Case api. Client Id will be the Client Id of App Registration - `spn-crm-case-management-integration-<env>`|
|ApiConnectionCommonDataService | `apicon-<sub>-apps-prdcds-<env>-we-01` | API Connection to Common Data Service for market place product api. Client Id will be the Client Id of App Registration - `spn-crm-general-integration-<env>`|
|ApiConnectionCommonDataService | `apicon-<sub>-apps-pflcds-<env>-we-01` | API Connection to Common Data Service for profile and organisation profile api. Client Id will be the Client Id of App Registration - `spn-crm-profile-management-integration-<env>`|
|ApiConnectionLogAnalytics | `apicon-<sub>-apps-log-<env>-we-01` | API Connection to Log Analytics - 'log-<sub>-pltf-<env>-we-01'|
|AppServicePlan | `plan-<sub>-apps-int-<env>-we-01`||
|EventGridDomain | `egd-<sub>-apps-int-<env>-we-01`||
|FunctionAppBPA | `func-<sub>-apps-intbpa-<env>-we-01` | Function App to subscribe and process the Sharepoint data|
|FunctionAppNTF | `func-<sub>-apps-intntf-<env>-we-01` | Function App to track the changes of Sharepoint data|
|FunctionAppCE | `func-<sub>-apps-acm-<env>-we-01` | Function app to monitor consumption metering storage for 6D|
|LogicApp | `logic-<sub>-apps-qnacopy-<env>-we-01` | QnAMaker FAQ copier from source to destination
|LogicApp | `logic-<sub>-apps-qnakbsync-<env>-we-01` | QnAMaker Knowledge articles Synchronizer
|LogicApp | `logic-<sub>-apps-inttrsl-<env>-we-01` | Logic app to create Translation Task and do Auto Translation from English to Arabic of Sharepoint data|
|LogicApp | `logic-<sub>-apps-intaprv1-<env>-we-01` | This logic app is responsible creating approval task which needs to be approved by Content approvers based on the content sensitivity. |
|LogicApp | `logic-<sub>-apps-intgbaprl-<env>-we-01` |This logic app is responsible for creating approval task which needs to be approved by marketplace content approvers.|
|LogicApp |`logic-<sub>-apps-intprdt-<env>-we-01` | Logic app to sync Products from CRM|
|LogicApp | `logic-<sub>-apps-intsec-<env>-we-01` | Logic app to sync Global Sectors List from CRM|
|LogicApp | `logic-<sub>-apps-secsync-<env>-we-01` | Logic app to sync Global Sectors List with Sharepoint Taxonomy terms|
|LogicApp | `logic-<sub>-apps-route-<env>-we-01`| This Logic App uses the 2019-05-01 version of the module to allow for Access Control configuration.  **Important:** after the APIM resource for this Logic App has been deployed (`apim-<sub>-shrd-<env>-we-01`), update the accessControl parameter in the ARM template for this resource to the Public IP of the APIM in the CIDR format. For example, if the Public IP of APIM is <code>1.1.1.1</code>, then replace the value in the ARM template with <code>1.1.1.1/32</code>. If this is not done, the Logic App will return an error stating that the IP is not allowed to access the Logic App trigger.|
|LogicApp | `logic-<sub>-apps-6dbill-<env>-we-01`|Receives 6DBilling from the Service Bus Queue and forwards it onto the Event Domain. No processing is needed on the Event before passing so it just acts as a forwarder.|
|LogicApp | `logic-<sub>-apps-6dhook-<env>-we-01`| Depends on Client Secret of Central Platform Core APIs which has to be seeded from `kv-<sub>-apps-<env>-we-01`|
|LogicApp | `logic-<sub>-apps-mpsidx-<env>-we-01`|The data that was generated from CRM and CMS will be saved to Azure Search via Events. The data here is for products, KB articles and news. This Logic App uses the 2019-05-01 version of the module to allow for Access Control configuration. Access Control has been configured to only allow other Logic Apps to trigger this app. |
|LogicApp | `logic-<sub>-apps-mpsd365-<env>-we-01`|It triggers when message is received on event trigger domain topic and subscribed to product - create, update, delete and Kbarticle - create, update, delete and send to     `logic-<sub>-apps-mpsidx-<env>-we-01`|
|LogicApp | `logic-<sub>-apps-mpso365-<env>-we-01`|It triggers when message is received on event trigger domain topic and subscribed to news - create, update, delete and send to `logic-<sub>-apps-mpsidx-<env>-we-01`.|
|LogicApp | `logic-<sub>-apps-dfndr-<env>-we-01` | Logic app triggers when a malware file is uploaded in Blob container and update the attachment extension entity Is Unsafe as true.
|LogicApp | `logic-<sub>-apps-intfile-<env>-we-01` | Logic app retrieves the content of file from Blob container and update the file content in D365.|
|LogicApp | `logic-<sub>-apps-intsubs-<env>-we-01`| Logic app performs upsert operation on Market Place Product Subscription.|
|LogicApp | `logic-<sub>-apps-intacnt-<env>-we-01` | Logic app performs update operation on organisation and profile.|
|LogicApp | `logic-<sub>-apps-apimt-<env>-we-01` | Logic app queries APIM daily to get subscriptions usage information and sends event. Requires the `spn-armapi-reader-<env>` Service Principal and the `ARMAPI-ClientSecret` secret to be seeded. |
|ServiceBusNamespace | `sb-<sub>-apps-int-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intprodsync-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intntf-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intsec-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-int6dbill-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intd365-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-into365-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intchglog-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intaprvl-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intgbaprl-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intcoreapi-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-qnaadd-<env>-we-01`||
|ServiceBusNamespaceQueue | `sbq-<sub>-apps-intiotalert-<env>-we-01`||
|ServiceBusNamespaceTopic | `sbt-<sub>-apps-qnasync-<env>-we-01`||
|ServiceBusNamespaceTopic Subscription | `sbts-<sub>-apps-copyqna-<env>-we-01`||
|StorageAccounts | `st<sub>appsint<env>we01`||

### 4.4.4 Post deployment steps
- If its a fresh deployment follow these steps:
1. In the Azure portal search for `apicon-<sub>-apps-intspo-<env>-we-01` and open it.
2. Click on Edit Api Connection under General tab in the right panel.
3. Click on Authorize to and authorize the connection using cms.automation account's credentials .
4. Repeat the above three steps for `apicon-<sub>-apps-into365-<env>-we-01`
5. Change the value of "**deploy**" parameter to "**false**" in `apicon-<sub>-apps-intspo-<env>-we-01-parameters.json`and `apicon-<sub>-apps-into365-<env>-we-01-parameters.json`
6. If the value of "deploy" is "false" then we don't need to reauthenticate the api connections on subsequent deployments.  
6. Update the accessControl ARM parameter of `logic-<sub>-apps-route-<env>-we-01` with the Public IP of `apim-<sub>-shrd-<env>-we-01` once APIM is deployed. See the remarks of `logic-<sub>-apps-route-<env>-we-01` above for more details. 

### 4.4.5 Verify Event Topic Subscriptions 
In `egd-<sub>-apps-int-<env>-we-01`
Verify that following subscriptions are created in the event grid domain topics
|Topic| Subscription|
|--|--|
|coreapi|`logic-<sub>-apps-intfile-<env>-we-01-sub`|
|d365|`logic-<sub>-apps-6dhook-<env>-we-01-sub`|
|d365|`logic-<sub>-apps-mpsd365-<env>-we-01-sub`|
|d365|`logic-<sub>-apps-intprdt-<env>-we-01-sub`|
|d365|`logic-<sub>-apps-intsec-<env>-we-01-sub`|
|d365|`logic-<sub>-apps-qnakbsync-<env>-we-01-sub`|
|o365|`logic-<sub>-apps-mpso365-<env>-we-01-sub`|
|6dbilling|`logic-<sub>-apps-intacnt-<env>-we-01-sub`|
|6dbilling|`logic-<sub>-apps-intsubs-<env>-we-01-sub`|


## 4.5 Shared Resource Group 
### 4.5.1 Resource Group
`rg-<sub>-shrd-<env>-we-01`
### 4.5.2 Dependencies
1. `rg-<sub>-shrd-mon-<env>-we-01`
1. `rg-<sub>-pltf-net-<env>-we-01`
1. `rg-<sub>-apps-int-<env>-we-01`
1. `rg-<sub>-pltf-sec-<env>-we-01`
1. Self hosted agent
1. Certificates uploaded to `kv-<sub>-pltf-<env>-we-01`

### 4.5.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApiManagement| `apim-<sub>-shrd-<env>-we-01` | hostConfigurations parameter should be empty for initial deployment|
|ContentDeliveryNetwork | `cdn-<sub>-shrd-<env>-we-01` ||
|ContentDeliveryNetworkEndpoint | `<env>-tasmu`||
|StorageAccount | `st<sub>shrd<env>we01` ||


### 4.5.4 Update Key Vault Access Policies 
for `kv-<sub>-pltf-<env>-we-01`

|Object Id| Secrets |  Certificates|
|--|--|--|
|`apim-<sub>-shrd-<env>-we-01`|Get,List||

Redeploy `rg-<sub>-pltf-sec-<env>-we-01`

### 4.5.5 Add Custom Domains to APIM
Update the parameter file - `apim-<sub>-shrd-<env>-we-01` for hostConfigurations
```
"hostnameConfigurations":{
   "value": [
      {
         "type": "DeveloperPortal",
         "hostName": "developer.<env>.sqcp.qa",
         "keyVaultId": "https://kv-<sub>-pltf-<env>-we-01.vault.azure.net/secrets/<env>-SQCP-Certificate",
         "negotiateClientCertificate": false,
         "defaultSslBinding": false
      },
      {
         "type": "Proxy",
         "hostName": "api.<env>.sqcp.qa",
         "keyVaultId": "https://kv-<sub>-pltf-<env>-we-01.vault.azure.net/secrets/<env>-SQCP-Certificate",
         "negotiateClientCertificate": false,
         "defaultSslBinding": true
      },
      {
         "type": "Management",
         "hostName": "api-management.<env>.sqcp.qa",
         "keyVaultId": "https://kv-<sub>-pltf-<env>-we-01.vault.azure.net/secrets/<env>-SQCP-Certificate",
         "negotiateClientCertificate": false,
         "defaultSslBinding": false
      }
   ]4.6.2
}
```

### 4.5.6 Add Integration APIs
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApiManagementLogicAppBackend | `apimlab-<sub>-shrd-<env>-we-01`||
|ApiManagementAPI | `apimapi-<sub>-shrd-<env>-we-01` | Refer module specific read me|

### 4.5.7 Add CMS Notification APIs
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApiManagementFunctionAppBackend | `apimfab-<sub>-shrd-<env>-we-01`|Refer module specific read me|
|ApiManagementCMSNotificationAPI | `apimcms-<sub>-shrd-<env>-we-01` | Refer module specific read me|


### 4.5.8 Redeploy Sshared Resource Group
`rg-<sub>-shrd-<env>-we-01`
### 4.5.9 Update the public IP of APIM
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|LogicApp | `logic-<sub>-apps-route-<env>-we-01` | Update the public IP of APIM for access|

### 4.5.10 Redeploy Integration Resource Group
`rg-<sub>-apps-int-<env>-we-01`

## 4.6 Apps AKS Resource Group
### 4.6.1 Resource Group 
`rg-<sub>-apps-aks-<env>-we-01`
### 4.6.2 Dependencies
1. `rg-<sub>-apps-mon-<env>-we-01`
1. `rg-<sub>-glob-npd-we-01`
1. `rg-<sub>-pltf-net-<env>-we-01`1. `rg-<sub>-apps-str-<env>-we-01`
### 4.6.3 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ManagedClusterCNI | `aks-<sub>-apps-<env>-we-01` ||
|ManagedIdentity | `mi-<sub>-apps-aks-<env>-we-01` | Deployed in `rg-<sub>-apps-aksnode-<env>-we-01` |
|ApplicationGateway | `agw-<sub>-apps-aks-<env>-we-01` | SKU and Tier - Standard_v2, firewallenabled - false|

## 4.7 Apps CKAN Resource Group
### 4.7.1 Resource Group
`rg-<sub>-apps-ckan-<env>-we-01`
### 4.7.2 Dependencies
1. `rg-<sub>-apps-net-<env>-we-01`
1. `rg-<sub>-apps-sec-<env>-we-01`
1. `rg-<sub>-apps-mon-<env>-we-01`
1. `rg-<sub>-pltf-net-<env>-we-01`
1. `rg-<sub>-pltf-sec-<env>-we-01`
1. Certificates uploaded to `kv-<sub>-pltf-<env>-we-01`
1. Secrets seeded in `kv-<sub>-apps-<env>-we-01`
### 4.7.3 Notes
Refer `kv-<sub>-pltf-<env>-we-01` and `mi-<sub>-pltf-<env>-we-01` for ssl certificates
### 4.7.4 Resources
| Module Name | Resource Name | Remarks |
|--|--|--|
| BitnamiCkan | `ckan-<sub>-apps-<env>-we-01` | check module specific read me for more details |
| ApiConnectionAzureBlob | `apicon-<sub>-apps-dlszn-<env>-we-01` | |
| ApiConnectionKeyVault | `apicon-<sub>-apps-ckankv-<env>-we-01` | |
| IntegrationAccount | `intac-<sub>-apps-ckan-<env>-we-01` | check module specific read me for more details|
| LogicApp | `logic-<sub>-apps-purvckan-<env>-we-01` | |
| FunctionAppCKAN | `func-<sub>-apps-ckan-<env>-we-01` | |
| AppServicePlan | `plan-<sub>-apps-ckan-<env>-we-01` | |

## 4.8 Apps WAF Resource Group
### 4.8.1 Resource Group
`rg-<sub>-apps-waf-<env>-we-01`
### 4.8.2 Dependencies 
1. `rg-<sub>-apps-mon-<env>-we-01`
1. `rg-<sub>-pltf-net-<env>-we-01`
1. `rg-<sub>-pltf-sec-<env>-we-01`
1. Certificates uploaded to `kv-<sub>-pltf-<env>-we-01`
### 4.8.3 Notes
Refer `kv-<sub>-pltf-<env>-we-01` and `mi-<sub>-pltf-<env>-we-01` for ssl certificates
### 4.8.4 Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApplicationGateway | `agw-<sub>-apps-api-<env>-we-01` | Refer private IP of `apim-<sub>-shrd-<env>-we-01` in backend pool|
|ApplicationGateway | `agw-<sub>-apps-web-<env>-we-01` |Refer private IP of `agw-<sub>-apps-aks-<env>-we-01` and `agw-<sub>-apps-ckan-<env>-we-01` in backend pools |
|ApplicationGateway | `agw-<sub>-apps-ntf-<env>-we-01` |Refer private IP of `apim-<sub>-shrd-<env>-we-01` in backend pool|

## 4.9 Apps Payment Token Resource Group
### 4.9.1 Resource Group
`rg-<sub>-apps-pt-<env>-we-01`
### 4.9.2 Dependencies
1. `rg-<sub>-apps-mon-<env>-we-01`
### 4.9.3 Resources 
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|KeyVault | `kv-<sub>-apps-pt-<env>-we-01` ||
|AppServicePlan | `plan-<sub>-apps-pt-<env>-we-01` ||
|FunctionAppPt | `func-<sub>-apps-pt-<env>-we-01`||

## 4.10 Update Key Vault Access Policies 
for `kv-<sub>-apps-pt-we-01`
Redeploy `rg-<sub>-apps-pt-<env>-we-01`

|Object Id| Secrets |  Certificates|
|--|--|--|
|`func-<sub>-apps-pt-<env>-we-01`|Get, List, Set||


## 4.11 Update Key Vault Access Policies
`kv-<sub>-apps-<env>-we-01`
Redeploy `rg-<sub>-apps-sec-<env>-we-01`

|Object Id| Secrets |  Certificates|
|--|--|--|
|`mi-<sub>-apps-aks-<env>-we-01`|Get||
|`func-<sub>-apps-acm-<env>-we-01`|Get||
|`app-<sub>-apps-bot-<env>-we-01`|Get||
|`func-<sub>-apps-qnasync-<env>-we-01`|Get||
|`func-<sub>-apps-luistra-<env>-we-01`|Get||
|`func-<sub>-apps-intntf-<env>-we-01`|Get||
|`func-<sub>-apps-acm-<env>-we-01`|Get||
|`func-<sub>-apps-intbpa-<env>-we-01`|Get|Get|
|`func-<sub>-apps-pt-<env>-we-01`|Get||
|`func-<sub>-apps-ckan-<env>-we-01`|Get||

## 4.12 Seeding secrets to Key Vault 
`kv-<sub>-apps-<env>-we-01`
Prepare [library variable group](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library?itemType=VariableGroups) in Azure DevOps by copying one of the existing variable groups - <env>
[Update the secret values after retrieval](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/151/Key-Vault-Secrets-Apps)
The list of secrets to be seeded to `kv-<sub>-apps-<env>-we-01` - Scripts\KeyVault\all-secrets.yml
Stage for `<env>` must be added to pipeline and run the pipeline to populate key vault - [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) (Uses powershell commands to import)

## 4.13 Adding Configurations to App Config Store 
`acst-<sub>-apps-str-<env>-we-01`
The configurations and their retrieval - Scripts\AppConfigurations
Add application configurations for `<env>`.
Placeholders already present for all env
Add stage for `<env>` to the app configuration seeding pipeline - [CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406) (Uses powershell commands to import)

## 4.14 Link AKS Cluster DNS Zone to CPH Subscription
1. A user account being used should have access to both the subscriptions 
1. Go to AKS node resource group (`rg-<sub>-apps-aksnode-<env>-we-01`)
1. Open the private DNS Zone
1. Go to virtual network links and add link as below
![image.png](/.attachments/image-ae0af3f0-3406-4327-bf7f-2d29bfa8c5c4.png)

## 4.15 Role Assignments 
Update role assignment for  following resources

|Identity Name| Type  | Target Resource | Role |
|--|--|--|--|
|  `func-<sub>-apps-luistra-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`func-<sub>-apps-qnasync-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`func-<sub>-apps-intbpa-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`func-<sub>-apps-intntf-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`func-<sub>-apps-pt-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`func-<sub>-apps-ckan-<env>-we-01` | Function App  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`app-<sub>-apps-bot-<env>-we-01` | App Service  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader ||`spn-cmsbpa-<env>` | Service Principal | `<env>-cdntasmu` | CDN Endpoint Contributor |
|`mi-<sub>-apps-aks-<env>-we-01` | User Assigned Managed Identity  | `acst-<sub>-apps-str-<env>-we-01` | App Configuration Store Data Reader |
|`mi-<sub>-apps-aks-<env>-we-01 `| User Assigned Managed Identity | `rg-<sub>-apps-aks-<env>-we-01` | Reader |
|`mi-<sub>-apps-aks-<env>-we-01 `| User Assigned Managed Identity | `agw-<sub>-apps-aks-<env>-we-01` | Contributor |
|`mi-<sub>-apps-aks-<env>-we-01` | User Assigned Managed Identity | `rg-<sub>-apps-aksnode-<env>-we-01` | Reader |
|`mi-<sub>-apps-aks-<env>-we-01` | User Assigned Managed Identity | `aks-<sub>-apps-<env>-we-01-agentpool` | Managed Identity Operator |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity | `agw-<sub>-apps-aks-<env>-we-01` | Contributor |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity | `acr<sub>globnpdwe01` | Acr Pull |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity | `rg-<sub>-apps-aksnode-<env>-we-01` | Virtual Machine Contributor |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity | `rg-<sub>-apps-aksnode-<env>-we-01` | Managed Identity Operator |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity | `rg-<sub>-apps-aksnode-<env>-we-01`| Managed Identity Contributor |
|`aks-<sub>-apps-<env>-we-01-agentpool` | User Assigned Managed Identity  | `vnet-<sub>-pltf-<env>-we-01/snet-<sub>-apps-aks-<env>-we-01` | Network Contributor |
|`spn-cmsbpa-<env>`|Service Principal|`<env>-cdntasmu`|CDN Endpoint Contributor. **Note**: Use `spn-cmsbpa-dev` for environments upto uat and `spn-cmsbpa-prod` for pre prod and prod. The app must be present in the same directory where azure subscription is present.|
|`spn-armapi-reader-<env>`|Service Principal|`apim-<sub>-shrd-<env>-we-01`|Reader|

## 4.16 Configuring Notification Hubs for FCM and APNS
1. Obtain the API Key of [Google Firebase Cloud Account](https://console.firebase.google.com/) after creating the project from project settings
1. Obtain the p12 certificate by Developer Account into the development Mac machine. Follow the steps to [export the certificate](https://help.attendify.com/en/articles/613466-how-to-export-a-push-notification-apns-certificate-in-a-p12-file#:~:text=Generate%20APNS.p12%20certificate%20Double%20click%20the%20Development%20certificate,app%20certificate%20and%20right%20click%20to%20export%20it.)  in .p12 format. 
3. Go to notification hub (`ntf-<sub>-apps-str-<env>-we-01`) -> Settings
3.1. Update the Google in Settings with the API Key obtained.
3.2. Update the Apple in Settings for iOS Certificate. For production environment, use the application mode as production.
1. Test Send (Support and troubleshooting) for Apple and Android Phone for verifications.

# 5 Deployment of Private Endpoints
## Dependencies
1. Private DNS Zones deployed
## 5.1 Add service endpoints to subnets 
1. Update `vnet-<sub>-pltf-<env>-we-01` ARM template for adding service endpoints to subnets.
```
 "subnets": {
            "value": [
                {
                    "name": "snet-<sub>-apps-aks-<env>-we-01",
                    "addressPrefix": "172.20.72.0/23",
                    "networkSecurityGroupName": "nsg-<sub>-apps-aks-<env>-we-01",
                    "routeTableName": "route-<sub>-apps-aks-<env>-we-01",
                    "serviceEndpoints": [
                        {
                            "service": "Microsoft.AzureCosmosDB",
                            "locations": [
                                "westeurope"
                            ]
                        },
                        {
                            "service": "Microsoft.ServiceBus",
                            "locations": [
                                "westeurope"
                            ]
                        }
                    ],
                    "delegations": [],
                    "nsgsRGName": "rg-<sub>-apps-sec-<env>-we-01",
                    "routesRGName": "rg-<sub>-apps-net-<env>-we-01"
                },
                {
                    "name": "snet-<sub>-apps-bkend-<env>-we-01",
                    "addressPrefix": "172.20.82.192/26",
                    "networkSecurityGroupName": "nsg-<sub>-apps-bkend-<env>-we-01",
                    "routeTableName": "route-<sub>-apps-bkend-<env>-we-01",
                    "serviceEndpoints": [
                        {
                            "service": "Microsoft.AzureCosmosDB",
                            "locations": [
                                "westeurope"
                            ]
                        },
                        {
                            "service": "Microsoft.ServiceBus",
                            "locations": [
                                "westeurope"
                            ]
                        }
                    ],
                    "delegations": [],
                    "nsgsRGName": "rg-<sub>-apps-sec-<env>-we-01",
                    "routesRGName": "rg-<sub>-apps-net-<env>-we-01"
                }
            ]
 }
```
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|VirtualNetwork| `vnet-<sub>-pltf-<env>-we-01` ||

## 5.3 Add private endpoints to resources
1. Add template for private endpoint like `prvep-<sub>-apps-cosmos-<env>-we-01`

| Module Name | Parameter File Name | Remarks |
|--|--|--|
|PrivateEndpoint| `prvep-<sub>-apps-cosmos-<env>-we-01` ||
|PrivateEndpoint| `prvep-<sub>-apps-sbstrntf-<env>-we-01` ||

2. Run [`CD-rg-<sub>-apps-net-<env>-we-01`](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)



# 6 Deployment of the solution components

## 6.1 Deploy Platform APIs
### 6.1.1 Dependencies
1. Self Hosted Agent
1. [Library](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library) variable group - <env> updated with variable and secrets
1. Role Assignments applied as per [table](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=4.14-role-assignments)
1. Service Connection for Azure Container Registry and Azure Resource Manager for AKS

### 6.1.2 [Addding a new environment for platform apis](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/platform-apis?anchor=adding-a-new-environment)
- [CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)
- [CD-PlatformAPIs-Prd-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1021)


## 6.2 Deploy Web Apps
### 6.2.1 Dependencies
1. Self Hosted Agent
1. [Library](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library) variable group - <env> updated with variable and secrets
1. Service Connection for Azure Resource Manager

### 6.2.2 [Update web apps pipelines for new environments](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/web-apps?path=%2F&version=GBmaster&_a=contents&anchor=adding-a-new-environment)
- [CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)
- [CD-WebApps-Prd-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1020)

## 6.3 Deploy Chatbot Solutions
### 6.3.1 Dependencies
1. Self Hosted Agent
1. [Library](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library) variable group - <env> updated with variable and secrets 
1. Service Connection for Azure Resource Manager
### 6.3.2 [Detailed Steps](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=webapp-bot-ad-update)

## 6.4 Update APIM Pipelines
### 6.4.1 Dependencies
1. Self Hosted Agent
1. Custom Domains Updated
1. [Library](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library) variable group - <env> updated with variable and secrets (Azure-Search-Key, Bot-Directline-Key)
1. `rg-<sub>-apps-waf-<env>-we-01`
1. Service Connection connecting the APIM

### 6.4.2 [Update APIM Pipelines for new environments](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/apim-api-config?anchor=adding-a-new-environment)
### 6.4.3 Enable access for required products on APIM
![image.png](/.attachments/image-5ac68024-d75d-42dc-a25b-b9e3402c8f3e.png)
### 6.4.4 Delete default products "Starter" and "unlimited" on APIM from above screenshot.