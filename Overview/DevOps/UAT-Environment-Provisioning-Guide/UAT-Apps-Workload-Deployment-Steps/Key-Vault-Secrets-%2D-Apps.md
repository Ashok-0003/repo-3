
|Key Vault Name| Name  | Type | How to Retrieve | Remarks|
|--|--|--|--|--|
|kv-cpd-apps-<env>-we-01|AdminPortal-ADAuth-ClientSecret|Secret|Create Client Secret for adminportal app registration in B2C Tenant under certificates and secrets menu.||
|kv-cpd-apps-<env>-we-01|AdminPortal-AuthClaims-GroupId|Secret|Create "Platformadmin" Group in Azure Ad and retrieve the object Id of the group.||
|kv-cpd-apps-<env>-we-01|Azure-Search-Key|Secret|Primary Admin key of resource srch-cpd-apps-cog-<env>-we-01 ||
|kv-cpd-apps-<env>-we-01|BotAppSecret|Secret|||
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisAuthSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luiauth-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisRtSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luisrt-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaEnSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-qna-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaArSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-arqna-<env>-we-01** | | 
|kv-cpd-apps-<env>-we-01|CDNSettings-StorageAccount|Secret|||
|kv-cpd-apps-<env>-we-01|Cms-Function-ServiceBusConnectionString| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**|
|kv-cpd-apps-<env>-we-01|Cms-Function-NotificationUrl| Secret |Default(Function Key) Function URL of notify function in **func-cpd-apps-intntf-<env>-we-01**|Only available after [CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301) pipeline is succeeded|
|kv-cpd-apps-<env>-we-01|Cms-Function-TenantId| Secret |Directory (tenant) ID of Azure AD App **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientId| Secret |Application (client) ID of Azure AD app **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePassword| Secret |**CMSBPA** certificate password|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePfxKey| Secret |**CMSBPA** certificate pfx key|
|kv-cpd-apps-<env>-we-01|CDNSettings-StorageAccount| Secret |Connection string of the resource **stcpdshrd<env>we01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-ConsumptionStorageAccount|Secret|||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-CosmosDBAuthKey|Secret|||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-DynamicsSql|Secret|||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-DynamicsSqlExport|Secret|||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FieldServiceServiceBus| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FileStorageAccount| Secret |Connection string for **stcpdappsstr<env>we01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IntegrationServiceBus| Secret |Send,Listen access policy connection string of the resource sb-cpd-apps-int-<env>-we-01 for deployment||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IoTHub| Secret |Retrieve connection string from **iot-cpd-data-<env>-we-01** -> **Shared access policies** -> **registryRead** -> **Connection-String-Primary Key**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-NotificationHub| Secret |||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-Redis| Secret |||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-SmartParkingSQLDB| Secret |Form the connection string for sql-cpd-data-<env>-we-01|Eg.`Data Source=sql-cpd-data-<env>-we-01.database.windows.net;Initial Catalog=sqldb-cpd-data-<env>-we-01;User Id=<userId>;Password=<pwd>`|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-StorageAccount| Secret |||
|kv-cpd-apps-<env>-we-01|Crm-CaseManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Case api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-case-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-Common-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for common dynamic connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-common-integration-test <p>Client Secret : **********</p><p> TEST - spn-crm-common-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-general-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-ProfileManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Profile api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-profile-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|EventGridSettings-DomainKey| Secret |Secret stored in kv-cpd-apps-<env>-we-01 used for Event Grid Domain Key, retrieve value from Azure Event Grid Domain egd-cpd-apps-int-<env>-we-01||
|kv-cpd-apps-<env>-we-01|GraphClientSecret| Secret |||
|kv-cpd-apps-<env>-we-01|ManageEventFunction-AzureADOptions-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for ManageEvent Function connection, generate secret from Azure AD app registration.||
|kv-cpd-apps-<env>-we-01|Mobile-AppCenterDroidKey| Secret |||
|kv-cpd-apps-<env>-we-01|Mobile-AppCenterIosKey| Secret |||
|kv-cpd-apps-<env>-we-01|Mobile-CmsSubscriptionKeyName| Secret |||
|kv-cpd-apps-<env>-we-01|Mobile-NotificationHubListenConn| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-AuthKey| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-AuthToken| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-AzureADOptions-ClientSecret| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-GSMSKey| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-NotificationServiceBusConnectionString| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-SmsApiName| Secret |||
|kv-cpd-apps-<env>-we-01|NotificationSettings-SmsApiPassword| Secret |||
|kv-cpd-apps-<env>-we-01|OrganisationApi-AzureADOptions-ClientSecret| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AuthorizeCard-ClientSecret| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AuthorizeCard-Password| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-GetPaymentPreferenceServiceURL| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-TerminalPwd| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-Token| Secret |||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AzureAd-ClientSecret| Secret |||
|kv-cpd-apps-<env>-we-01|PowerBIEmbed-UpdatePaymentPreferenceServiceURL| Secret |||
|kv-cpd-apps-<env>-we-01|SmartParking-ADAuth-ClientSecret| Secret |Client Secret fo Smart Parking APi App regestration in B2C tenant||
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint| CMSBPA Self signed certificate|
|kv-cpd-apps-<env>-we-01|Cms-Api-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint|CMSAPI Self signed certificate| 