
|Key Vault Name| Name  | Type | How to Retrieve | Remarks|
|--|--|--|--|--|
|kv-cpd-apps-<env>-we-01|Cms-Function-ServiceBusConnectionString| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**|
|kv-cpd-apps-<env>-we-01|Cms-Function-NotificationUrl| Secret |Default(Function Key) Function URL of notify function in **func-cpd-apps-intntf-<env>-we-01**|Only available after [CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301) pipeline is succeeded|
|kv-cpd-apps-<env>-we-01|Cms-Function-TenantId| Secret |Directory (tenant) ID of Azure AD App **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientId| Secret |Application (client) ID of Azure AD app **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePassword| Secret |**CMSBPA** certificate password|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePfxKey| Secret |**CMSBPA** certificate pfx key|
|kv-cpd-apps-<env>-we-01|CDNSettings-StorageAccount| Secret |Connection string of the resource **stcpdshrd<env>we01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FieldServiceServiceBus| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FileStorageAccount| Secret |Connection string for **stcpdappsstr<env>we01**||
|kv-cpd-apps-<env>-we-01|Crm-CaseManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Case api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-case-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-Common-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for common dynamic connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-common-integration-test <p>Client Secret : **********</p><p> TEST - spn-crm-common-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-general-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-ProfileManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Profile api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-profile-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IntegrationServiceBus| Secret |Send,Listen access policy connection string of the resource sb-cpd-apps-int-<env>-we-01 for deployment||
|kv-cpd-apps-<env>-we-01|EventGridSettings-DomainKey| Secret |Secret stored in kv-cpd-apps-<env>-we-01 used for Event Grid Domain Key, retrieve value from Azure Event Grid Domain egd-cpd-apps-int-<env>-we-01||
|kv-cpd-apps-<env>-we-01|ManageEventFunction-AzureADOptions-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for ManageEvent Function connection, generate secret from Azure AD app registration.||
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint| CMSBPA Self signed certificate|
|kv-cpd-apps-<env>-we-01|Cms-Api-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint|CMSAPI Self signed certificate| 
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisAuthSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luiauth-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisRtSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luisrt-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaEnSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-qna-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaArSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-arqna-<env>-we-01** | | 



