[[_TOC_]]
# Pre requisites
1. [Self Hosted Agents](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/159/Self-Hosted-Agents) equivalent to Microsoft Hosted Windows Agent provisioned in Central Platform Hub VNet to deploy APIM and AKS solutions
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

## Global Resources for a tenant
### 1. Global Non Production Resource Group
#### Resource Group
 [rg-cpd-glob-npd-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=393)
#### Dependencies
#### Resources
Azure AD B2C Tenant - tasmucpb2cnonprod.onmicrosoft.com 
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ContainerRegistry | acrcpdglobnpdwe01 | |
|KeyVault | kv-cpd-glob-npd-we-01 | |
|ManagedIdentity | mi-cpd-glob-npd-we-01 | |
|SendGrid | sga-cpd-glob-email-npd-we-01 | Silver Tier |

### 2. Global Consumption Metering Resource Group
#### Resource Group
[rg-cpd-glob-acm-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=479)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|StorageAccount | stcpdglobacmwe01 ||
[Create a daily export of azure consumption metering for 6D Billing](https://docs.microsoft.com/en-us/azure/cost-management-billing/costs/tutorial-export-acm-data?tabs=azure-portal#create-a-daily-export)

## Creation and set up of AD B2C Tenant
Refer the document uploaded on [Ooredoo Sharepoint](https://ooredooonline.sharepoint.com/:w:/s/TASMU-CentralPlatformPMO/EdIKRGu6E1VGnA-naCTSBXQBjgdtCiT9C6n5E9rehxUWmw?e=ZSX2Yf)

## Register the applications in AD and AD B2C
1. [AD B2C Registrations](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad-b2c)
2. [AAD Registrations](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad---tasmusqcp.onmicrosoft.com)

# Deployment of networking and monitoring infrastructure
### 1. Shared Monitoring Resource Group
#### Resource Group
 [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApplicationInsights | appi-cpd-shrd-mon-uat-we-01||
|AutomationAccounts | aut-cpd-shrd-mon-uat-we-01||
|EventHubNamespaces | evhns-cpd-shrd-mon-uat-we-01||
|LogAnalytics | log-cpd-shrd-mon-uat-we-01||
|StorageAccount | stcpdshrddiaguatwe01||

### 2. Apps Monitoring Resource Group
#### Resource Group
[rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApplicationInsights | appi-cpd-apps-mon-uat-we-01||
|AutomationAccounts | aut-cpd-apps-mon-uat-we-01||
|EventHubNamespaces | evhns-cpd-apps-mon-uat-we-01||
|LogAnalytics | log-cpd-apps-mon-uat-we-01||
|StorageAccount | stcpdappsdiaguatwe01||

### 3. Apps Security Resource Group
#### Resource Group
[rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
#### Dependencies
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|NetworkSecurityGroups | nsg-cpd-apps-aks-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-agw-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-agwweb-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-agwapi-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-agwntf-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-apim-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-bkend-uat-we-01||
|NetworkSecurityGroups | nsg-cpd-apps-testvms-uat-we-01||
|KeyVault | kv-cpd-apps-uat-we-01 | Access Policy added only for ADO Service Connection |

### 4. Apps Networking Resource Group
#### Resource Group
[rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|RouteTables | route-cpd-apps-aks-uat-we-01||
|RouteTables | route-cpd-apps-apim-uat-we-01||
|RouteTables | route-cpd-apps-bkend-uat-we-01||
|RouteTables | route-cpd-apps-testvms-uat-we-01||

### 5. Platform Networking Resource Group
#### Resource Group
[rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)

#### Dependencies
1. [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
1. [rg-cpd-apps-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=343)
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|VirtualNetwork | vnet-cpd-pltf-uat-we-01||

### 6. Platform Security Resource Group
#### Resource Group
[rg-cpd-pltf-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=356)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|KeyVault |kv-cpd-pltf-uat-we-01 |Access Policy added only for ADO Service Connection|
|ManagedIdentity |mi-cpd-pltf-uat-we-01 ||

### 7. Update Key Vault Access Policies - kv-cpd-pltf-uat-we-01
 redeploy [rg-cpd-pltf-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=356)

|Object Id| Secrets |  Certificates|
|--|--|--|
|mi-cpd-pltf-uat-we-01|Get|Get|


# Deployment of Apps Infrastructure
### 1. Apps Storage Resource Group
#### Resource Group
[rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
#### Dependencies
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|AppConfigurationStore|acst-cpd-apps-str-uat-we-01||
|CosmosAccount | cosmos-cpd-apps-str-uat-we-01||
|CosmosDBSQL | sql-cosmos-cpd-apps-str-ntf-uat-we-01||
|CosmosDBSQL| sql-cosmos-cpd-apps-str-pt-uat-we-01 ||
|CosmosDBSQL| sql-cosmos-cpd-apps-str-bot-uat-we-01||
|CosmosDBSQLContainer | sqlc-cosmos-cpd-apps-str-ntf-uat-we-01||
|CosmosDBSQLContainer | sqlc-cosmos-cpd-apps-str-botfb-uat-we-01||
|CosmosDBSQLContainer | sqlc-cosmos-cpd-apps-str-botrt-uat-we-01||
|CosmosDBSQLContainer | sqlc-cosmos-cpd-apps-str-botst-uat-we-01||
|CosmosDBSQLContainer | sqlc-cosmos-cpd-apps-str-pt-uat-we-01||
|NotificationHub | ntf-cpd-apps-str-uat-we-01||
|NotificationHubNamespace | ntfns-cpd-apps-str-uat-we-01||
|RedisCache | redis-cpd-apps-str-uat-we-01||
|ServiceBusNamespace| sb-cpd-apps-strntf-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strntfbulk-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strntfbulkdl-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strntfoutboundgsmssingle-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strntfsingle-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strsmsbulk-uat-we-01||
|ServiceBusNamespaceTopic| sbt-cpd-apps-strsmssingle-uat-we-01||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strntfbulk-uat-we-01 ||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strntfbulkdl-uat-we-01||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strntfoutboundgsmssingle-uat-we-01||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strntfsingle-uat-we-01||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strsmsbulk-uat-we-01||
|ServiceBusNamespaceTopicSubscription | sbts-cpd-apps-strsmssingle-uat-we-01||
|StorageAccount | stcpdappsstruatwe01||

### 2. Seed the Key Vault Secrets in kv-cpd-apps-uat-we-01
required in the cognitive and integration pipelines 

| Resource Name |Secret Name  | Key Vault Name | Usage|
|--|--|--|--|
|apicon-cpd-apps-intcds-uat-we-01|Crm-CaseManagement-DynamicsSettings-ClientSecret|kv-cpd-apps-uat-we-01| Client Secret of the [App Registration (spn-crm-case-management-integration-<env>)](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments) - to authenticate Common Data Service Connection|
|apicon-cpd-apps-prdcds-uat-we-01|Crm-Common-DynamicsSettings-ClientSecret|kv-cpd-apps-uat-we-01| Client Secret of the [App Registration (spn-crm-common-integration-<env>)](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments) - to authenticate Common Data Service Connection|
|apicon-cpd-apps-integ-uat-we-01|sqcp-ado-spn-client-id|kv-cpd-pltf-uat-we-01| Client Id of the service principal having contributor access on integration event grid domain  to authenticate event grid api connection
|apicon-cpd-apps-integ-uat-we-01|sqcp-ado-spn-client-secret|kv-cpd-pltf-uat-we-01| Client Secret of the service principal having contributor access on integration event grid domain to authenticate event grid api connection|

### 3. Apps Cognitive Resource Group
 ####Resource Group Name - [rg-cpd-apps-cog-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=497)
####Dependencies - 
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
1. [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
1. [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)
1. App Registration - spn-bot-<env>
#### Notes - 
1. Naming Convention- 
Naming convention has deviation because QnA Maker requires names for both App Service and Cognitive Service as identical. It was consulted with product team and it's an issue in QnA Maker. This is the reason why app service and cognitive service for QnaMaker are named as **appcog-cpd-apps-qna-uat-we-01** for English and **appcog-cpd-apps-arqna-uat-we-01** for Arabic.

2. Location -
 QnA resources -  app-cpd-apps-qna-uat-we-01 and app-cpd-apps-arqna-uat-we-01 are deployed in West US as that is the only supported location for resource type - QnA. 
More Information on this limiation - [Link](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra/pullrequest/3568)
#### Resources -
| Module Name | Parameter File Name | Remarks |
|--|--|--|
| AppServiceManagement | app-cpd-apps-qna-uat-we-01 | App service for English QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePropertiesQnA | app-cpd-apps-qna-uat-we-01 | App service for English QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePlanScale | scale-cpd-apps-cog-uat-we-01 | App service scale for Bot api App Service
| AppServiceManagement | app-cpd-apps-arqna-uat-we-01 | App service for Arabic QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServicePropertiesQnA | app-cpd-apps-arqna-uat-we-01 | App service for Arabic QnA - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
| AppServiceManagement | app-cpd-apps-bot-uat-we-01 | App service for Bot API
|AppServicePlan | plan-cpd-apps-cog-uat-we-01
| CognitiveServices | cog-cpd-apps-luisauth-uat-we-01 | Luis Authoring
| CognitiveServices | cog-cpd-apps-luisrt-uat-we-01 | Luis Runtime
| CognitiveServicesQna | cog-cpd-apps-qna-uat-we-01 | QnAMaker English - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
|CognitiveServicesQna | cog-cpd-apps-arqna-uat-we-01 | QnAMaker Arabic - Refer [Remark](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps&pageId=119&anchor=notes--)
|FunctionAppQna | func-cpd-apps-luistra-uat-we-01 | func app luis trainer
|FunctionAppQna | func-cpd-apps-qnasync-uat-we-01 | func app triggered by logic-cpd-apps-qnakbsync-uat-we-01
|LogicApp | logic-cpd-apps-qnacopy-uat-we-01 | QnAMaker FAQ copier from source to destination
|LogicApp | logic-cpd-apps-qnakbsync-uat-we-01 | QnAMaker Knowledge articles Synchronizer
|SearchService | srch-cpd-apps-cog-uat-we-01 | Search Service English Cognitive Service for QnAMaker
|SearchService | srch-cpd-apps-arcog-uat-we-01 | Search Service Arabic Cognitive service for QnAMaker
| WebappBot | bot-cpd-apps-uat-we-01 | appId is ClientID of App Registration spn-bot-<env>

### 4. Apps Integration Resource Group 
#### Resource Group
[rg-cpd-apps-int-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=498)

#### Dependencies
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
1. [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499) 
1. [rg-cpd-glob-acm-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=479)
1. Two secrets added to kv-cpd-pltf-uat-we-01
1. [rg-cpd-pltf-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=356)
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|APIConnection | apicon-cpd-apps-into365-uat-we-01 | API Connection to Office 365 Tenant (CMS)|
|ApiConnectionServiceBus | apicon-cpd-apps-intsb-uat-we-01 | API Connection to Service Bus|
|APIConnection | apicon-cpd-apps-intspo-uat-we-01 | API Connection to Sharepoint Online|
|ApiConnectionEventGrid | apicon-cpd-apps-integ-uat-we-01 | API Connection to Event Grid Domain|
|ApiConnectionKeyVault | apicon-cpd-apps-intkv-uat-we-01 ||
|ApiConnectionEventGridPublish | apicon-cpd-apps-integd-uat-we-01 | (Refer - kv-cpd-pltf-uat-we-01 for secret)
|ApiConnectionAzureBlob | apicon-cpd-apps-intst-uat-we-01||
|APIConnectionCognitiveService | apicon-cpd-apps-intcog-uat-we-01 | API Connection to Translator Cognitive Service|
|APIConnection | apicon-cpd-apps-ascalrt-uat-we-01 | API Connection to Azure Security Alert trigger.|
|ApiConnectionCommonDataService | apicon-cpd-apps-intcds-uat-we-01 | API Connection to Common Data Service for Case api.|
|ApiConnectionCommonDataService | apicon-cpd-apps-prdcds-uat-we-01 | API Connection to Common Data Service for market place product api.|
|AppServicePlan | plan-cpd-apps-int-uat-we-01||
|EventGridDomain | egd-cpd-apps-int-uat-we-01||
|FunctionAppBPA | func-cpd-apps-intbpa-uat-we-01 | Function App to subscribe and process the Sharepoint data|
|FunctionAppNTF | func-cpd-apps-intntf-uat-we-01 | Function App to track the changes of Sharepoint data|
|FunctionAppCE | func-cpd-apps-acm-uat-we-01 | Function app to monitor consumption metering storage for 6D|
|LogicApp | logic-cpd-apps-inttrsl-uat-we-01 | Logic app to create Translation Task and do Auto Translation from English to Arabic of Sharepoint data|
|LogicApp | logic-cpd-apps-intaprv1-uat-we-01 | Logic app for Level 1 Approval|
|LogicApp | logic-cpd-apps-intgbaprl-uat-we-01 | Logic app for Level 2 approval|
|LogicApp | logic-cpd-apps-intprdt-uat-we-01 | Logic app to sync Products from CRM|
|LogicApp | logic-cpd-apps-intsec-uat-we-01 | Logic app to sync Global Sectors List from CRM|
|LogicApp | logic-cpd-apps-secsync-uat-we-01 | Logic app to sync Global Sectors List with Sharepoint Taxonomy terms|
|LogicApp | logic-cpd-apps-route-uat-we-01||
|LogicApp | logic-cpd-apps-6dbill-uat-we-01||
|LogicApp | logic-cpd-apps-6dhook-uat-we-01||
|LogicApp | logic-cpd-apps-mpsidx-uat-we-01||
|LogicApp | logic-cpd-apps-mpsd365-uat-we-01||
|LogicApp | logic-cpd-apps-mpso365-uat-we-01||
|LogicApp | logic-cpd-apps-dfndr-uat-we-01 | Logic app triggers when a malware file is uploaded in Blob container and update the attachment extension entity Is Unsafe as true.
|LogicApp | logic-cpd-apps-intfile-uat-we-01 | Logic app retrieves the content of file from Blob container and update the file content in D365.|
|LogicApp | logic-cpd-apps-intsubs-uat-we-01 | Logic app performs upsert operation on Market Place Product Subscription.|
|ServiceBusNamespace | sb-cpd-apps-int-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intprodsync-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intntf-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intsec-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-int6dbill-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intd365-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-into365-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intchglog-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intaprvl-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intgbaprl-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intcoreapi-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-qnaadd-uat-we-01||
|ServiceBusNamespaceQueue | sbq-cpd-apps-intiotalert-uat-we-01||
|ServiceBusNamespaceTopic | sbt-cpd-apps-qnasync-uat-we-01||
|ServiceBusNamespaceTopic Subscription | sbts-cpd-apps-copyqna-uat-we-01||
|StorageAccounts | stcpdappsintuatwe01||
#### Post deployment steps:
1. In the Azure portal search for `apicon-cpd-apps-intspo-uat-we-01` and open it.
2. Click on `Edit Api Connection` under General tab in the right panel.
3. Click on `Authorize` to and authorize the connection using `cms.automation` account's credentials .
4. Repeat the above three steps for `apicon-cpd-apps-into365-uat-we-01`  
### 5. Shared Resource Group 
#### Resource Group
[rg-cpd-shrd-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=500)
#### Dependencies
1. [rg-cpd-shrd-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=454)
1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
1. [rg-cpd-apps-int-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=498)
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApiManagement| apim-cpd-shrd-uat-we-01 ||
|ApiManagementLogicAppBackend | apimlab-cpd-shrd-uat-we-01 ||
|ApiManagementAPI | apimapi-cpd-shrd-uat-we-01 ||
|ContentDeliveryNetwork | cdn-cpd-shrd-uat-we-01 ||
|ContentDeliveryNetworkEndpoint | uat-tasmu ||
|StorageAccount | stcpdshrduatwe01 ||

### 6. Apps AKS Resource Group
#### Resource Group 
[rg-cpd-apps-aks-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=496)
#### Dependencies
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
1. [rg-cpd-glob-npd-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=393)
1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
1. [rg-cpd-apps-str-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=499)
#### Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ManagedClusterCNI | aks-cpd-apps-uat-we-01 ||
|ManagedIdentity | mi-cpd-apps-aks-uat-we-01 | Deployed in rg-cpd-apps-aksnode-uat-we-01 |
|ApplicationGateway | agw-cpd-apps-aks-uat-we-01 ||

### 7. Apps WAF Resource Group
#### Resource Group
[rg-cpd-apps-waf-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=621)
#### Dependencies 
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
1. [rg-cpd-pltf-net-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=355)
1. [rg-cpd-pltf-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=356)
1. Certificated uploaded to kv-cpd-pltf-uat-we-01
#### Notes
Refer kv-cpd-pltf-uat-we-01 and mi-cpd-pltf-uat-we-01 for ssl certificates
####Resources
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|ApplicationGateway | agw-cpd-apps-api-uat-we-01 ||
|ApplicationGateway | agw-cpd-apps-web-uat-we-01 ||
|ApplicationGateway | agw-cpd-apps-ntf-uat-we-01 ||

### 8. Apps Payment Token Resource Group
#### Resource Group
[rg-cpd-apps-pt-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=726)
#### Dependencies
1. [rg-cpd-apps-mon-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=394)
#### Resources 
| Module Name | Parameter File Name | Remarks |
|--|--|--|
|KeyVault | kv-cpd-apps-pt-uat-we-01 ||
|AppServicePlan | plan-cpd-apps-pt-uat-we-01 ||
|FunctionAppPt | func-cpd-apps-pt-uat-we-01 ||

### 9. Update Key Vault Access Policies - kv-cpd-apps-pt-we-01
redeploy [rg-cpd-apps-pt-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=726)

|Object Id| Secrets |  Certificates|
|--|--|--|
|func-cpd-apps-pt-uat-we-01|Get, List, Set||


### 10. Update Key Vault Access Policies -kv-cpd-apps-uat-we-01
redeploy [rg-cpd-apps-sec-uat-we-01](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=344)

|Object Id| Secrets |  Certificates|
|--|--|--|
|mi-cpd-apps-aks-uat-we-01|Get||
|func-cpd-apps-acm-uat-we-01|Get||
|app-cpd-apps-bot-uat-we-01|Get||
|func-cpd-apps-qnasync-uat-we-01|Get||
|func-cpd-apps-luistra-uat-we-01|Get||
|func-cpd-apps-intntf-uat-we-01|Get||
|func-cpd-apps-acm-uat-we-01|Get||
|func-cpd-apps-intbpa-uat-we-01|Get|Get|

### 11. Seeding secrets to Key Vault (kv-cpd-apps-uat-we-01)
Prepare [library variable group](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library?itemType=VariableGroups) in Azure DevOps by copying one of the existing variable groups - uat
[Update the secret values after retrieval](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/151/Key-Vault-Secrets-Apps)
The list of secrets to be seeded to kv-cpd-apps-<env>-we-01 - Scripts\KeyVault\all-secrets.yml
Stage for uat must be added to pipeline and run the pipeline to populate key vault - [CD-KeyVaultSecrets-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=337) (Uses powershell commands to import)

### 12. Adding Configurations to App Config Store (acst-cpd-apps-str-uat-we-01)
The configurations and their retrieval - Scripts\AppConfigurations
Add application configurations for <env>.
Placeholders already present for all env
Add stage for <env> to the app configuration seeding pipeline - [CD-AppConfigurations-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=406) (Uses powershell commands to import)

## Link AKS Cluster DNS Zone to CPH Subscription
1. A user account being used should have access to both the subscriptions 
1. Go to AKS node resource group (rg-cpd-apps-aksnode-uat-we-01)
1. Open the private DNS Zone
1. Go to virtual network links and add link as below

![image.png](/.attachments/image-313a362b-dc66-4d5c-989b-61b8579b90a5.png)
## Role Assignments 

|Identity Name| Type  | Target Resource | Role |
|--|--|--|--|
|func-cpd-apps-luistra-<env>-we-01 | Function App  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader |
|func-cpd-apps-qnasync-<env>-we-01 | Function App  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader |
|func-cpd-apps-intbpa-<env>-we-01 | Function App  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader |
|func-cpd-apps-intntf-<env>-we-01 | Function App  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader |
|app-cpd-apps-bot-<env>-we-01 | App Service  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader ||spn-cmsbpa-dev | Service Principal | <env>-cdntasmu | CDN Endpoint Contributor |
|mi-cpd-apps-aks-<env>-we-01 | User Assigned Managed Identity  | acst-cpd-apps-str-<env>-we-01 | App Configuration Store Data Reader |
|mi-cpd-apps-aks-<env>-we-01 | User Assigned Managed Identity | rg-cpd-apps-aks-<env>-we-01 | Reader |
|mi-cpd-apps-aks-<env>-we-01 | User Assigned Managed Identity | agw-cpd-apps-aks-<env>-we-01 | Contributor |
|mi-cpd-apps-aks-<env>-we-01 | User Assigned Managed Identity | rg-cpd-apps-aksnode-<env>-we-01 | Reader |
|mi-cpd-apps-aks-<env>-we-01 | User Assigned Managed Identity | aks-cpd-apps-<env>-we-01-agentpool | Managed Identity Operator |
|aks-cpd-apps-<env>-we-01-agentpool | User Assigned Managed Identity | acrcpdglobnpdwe01 | Acr Pull |
|aks-cpd-apps-<env>-we-01-agentpool | User Assigned Managed Identity | rg-cpd-apps-aksnode-<env>-we-01 | Virtual Machine Contributor |
|aks-cpd-apps-<env>-we-01-agentpool | User Assigned Managed Identity | rg-cpd-apps-aksnode-<env>-we-01 | Managed Identity Operator |
|aks-cpd-apps-<env>-we-01-agentpool | User Assigned Managed Identity | rg-cpd-apps-aksnode-<env>-we-01 | Managed Identity Contributor |
|aks-cpd-apps-<env>-we-01-agentpool | User Assigned Managed Identity  | vnet-cpd-pltf-<env>-we-01/snet-cpd-apps-aks-<env>-we-01 | Network Contributor |
|spn-cmsbpa-**dev**|Service Principal|<env>-cdntasmu|CDN Endpoint Contributor|

## Configuring Notification Hubs for FCM and APNS
1. Go to notification hub (ntf-cpd-apps-str-<env>-we-01) -> Settings
1. Update the Google Settings for API Key
Obtain the Web API Key of [Google Firebase Cloud Account](https://console.firebase.google.com/) after creating the project from project settings
1. Developer Account into the development Mac machine. 
Follow the steps to [export the certificate](https://help.attendify.com/en/articles/613466-how-to-export-a-push-notification-apns-certificate-in-a-p12-file#:~:text=Generate%20APNS.p12%20certificate%20Double%20click%20the%20Development%20certificate,app%20certificate%20and%20right%20click%20to%20export%20it.)  in .p12 format. 
1. Update the Apple Settings for iOS Certificate. 
For production environment, use the application mode as production.
1. Test Send (Support and troubleshooting) for Apple and Windows Phone

# Deployment of the solution components
1. [Update APIM Pipelines for new environments](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/apim-api-config?anchor=adding-a-new-environment)
1. For platform apis, ingress controller helm-config needs to be added for new env and stage should be added to [CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141) pointing to the new env
```
- stage: Deploy_<env>
    displayName: Deploy <env> stage
    dependsOn: Build
    variables:
      - group: <env>
      - name: azureResourceGroup
        value: "rg-cpd-apps-aks-<env>-dev-we-01"
      - name: kubernetesCluster
        value: "aks-cpd-apps-<env>-we-01"
      - name: containerRegistry
        value: "acrcpdglobnpdwe01.azurecr.io"
      - name: appConfigConnection
        value: "https://acst-cpd-apps-str-<env>-we-01.azconfig.io"
      - name: podIdentity
        value: "mi-cpd-apps-aks-<env>-we-01"
      - name: podIdentityClientId
        value: ""
      - name: podIdentityResourceId
        value: "/subscriptions/<subscriptionId>/resourceGroups/rg-cpd-apps-aksnode-<env>-we-01/providers/Microsoft.ManagedIdentity/userAssignedIdentities/mi-cpd-apps-aks-<env>-we-01"
      - name: env
        value: "<env>"
    pool:
      name: "<agentPool>"
    jobs:
      - deployment: Deploy
        displayName: Deploy Dev APIs
        environment: "<env>"
        strategy:
          runOnce:
            deploy:
              steps:
                - task: HelmInstaller@1
                  inputs:
                    helmVersionToInstall: "3.2.1"

                - template: templates/helm-resources.yml
                  parameters:
                    updateHelmResources: false

                - template: templates/deploy-dapr.yml
                  parameters:
                    installDapr: true

                - template: templates/add-keda.yml
                  parameters:
                    addKeda: false

                - template: templates/deploy-apps.yml
```
1. For integration function apps, add stage to the following pipeline pointing to uat resources
[CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301)
1. For web apps, add stage to the following pipeline pointing to uat resources
[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)

1. [Deploying Chatbot solutions](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=webapp-bot-ad-update)

1. For deploying Payment Preference function to function app, add stage to the following pipeline 
[CD-PlatformFuncApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=738)