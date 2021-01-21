
|Key Vault Name| Name  | Type | How to Retrieve | Remarks|
|--|--|--|--|--|
|kv-cpd-apps-<env>-we-01|AdminPortal-ADAuth-ClientSecret|Secret| Retrieve Client Secret for adminportal app registration in B2C Tenant under certificates and secrets menu.||
|kv-cpd-apps-<env>-we-01|AdminPortal-AuthClaims-GroupId|Secret| Navigate to"Platformadmin" Group in Azure Ad Groups in B2C Tenant and retrieve the object Id of the group.||
|kv-cpd-apps-<env>-we-01|Azure-Search-Key|Secret|Primary Admin key of resource srch-cpd-apps-cog-<env>-we-01 ||
|kv-cpd-apps-<env>-we-01|BotAppSecret|Secret|  Create client secret for **bot-cpd-apps<env>-we-01** WebAppBot resource and paste the value in this key. | [Refer steps](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=webapp-bot-ad-update) |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisAuthSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luiauth-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-LuisRtSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **cog-cpd-apps-luisrt-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaEnSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-qna-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|Bot-AppSettings-QnaArSubscriptionKey| Secret | Primary key of the Azure Cognitive services resource **appcog-cpd-apps-arqna-<env>-we-01** | |
|kv-cpd-apps-<env>-we-01|CDNSettings-StorageAccount| Secret | Connection string of the resource **stcpdshrd<env>we01**|Eg `DefaultEndpointsProtocol=https;AccountName=stcpdshrduatwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|
|kv-cpd-apps-<env>-we-01|Cms-Function-ServiceBusConnectionString| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**|
|kv-cpd-apps-<env>-we-01|Cms-Function-NotificationUrl| Secret |Default(Function Key) Function URL of notify function in **func-cpd-apps-intntf-<env>-we-01**|Only available after [CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301) pipeline is succeeded|
|kv-cpd-apps-<env>-we-01|Cms-Function-TenantId| Secret |Directory (tenant) ID of Azure AD App **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientId| Secret |Application (client) ID of Azure AD app **spn-cmsbpa-<env>**|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePassword| Secret |**CMSBPA** certificate password|
|kv-cpd-apps-<env>-we-01|Cms-Function-CertificatePfxKey| Secret |**CMSBPA** certificate pfx key|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-ConsumptionStorageAccount|Secret|Connection string of the resource **stcpdglobacmwe01**|Eg `DefaultEndpointsProtocol=https;AccountName=stcpdglobacmwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-CosmosDBAuthKey|Secret| Settings-> Keys -> PrimaryKey **cosmos-cpd-apps-<env>-we-01** ||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-DynamicsSql|Secret| Connection string of Dynamics SQL export service database in the format below below. This can be replaced with [Dynamics TDS endpoint](https://powerapps.microsoft.com/en-us/blog/tabular-data-stream-tds-protocol-endpoint-for-common-data-service-cds/) when it become GA. <br/><br/> Server=tcp:sql-cpd-data-uat-we-01.database.windows.net,1433;Initial Catalog=sqldb-cpd-dynamics-data-uat-we-01;Persist Security Info=False;User ID=adminsa;Password=****;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30; ||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-DynamicsSqlExport|Secret| Connection string of Dynamics SQL export service database in the format below below. **This secret requires a tag with name as [organizationid](https://docs.microsoft.com/en-us/power-platform/admin/determine-org-id-name) of the target dynamics environment and tag value as respective Azure AD tenant id. <br/><br/> Server=tcp:sql-cpd-data-uat-we-01.database.windows.net,1433;Initial Catalog=sqldb-cpd-dynamics-data-uat-we-01;Persist Security Info=False;User ID=adminsa;Password=****;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30; ||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IntegrationServiceBus| Secret |Send,Listen access policy connection string of the resource sb-cpd-apps-int-<env>-we-01 for deployment||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IoTHub| Secret |Retrieve connection string from **iot-cpd-data-<env>-we-01** -> **Shared access policies** -> **registryRead** -> **Connection-String-Primary Key**| Eg. `HostName=iot-cpd-data-uat-we-01.azure-devices.net;SharedAccessKeyName=registryRead;SharedAccessKey=<key>`|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-NotificationHub| Secret | Retrieve connection string from **ntf-cpd-apps-str-{​​env}​​-we-01** -> **Access policies** -> **Policy name - DefaultFullSharedAccessSignature** -> **connection string** ||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-Redis| Secret | Primary connection string of redis-cpd-apps-str-<env>-we-01|Eg.`redis-cpd-apps-str-uat-we-01.redis.cache.windows.net:6380,password=<>=,ssl=True,abortConnect=False`|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-SmartParkingSQLDB| Secret |Form the connection string for **sql-cpd-data-<env>-we-01** with provided userid and pwd in example.|Eg.`Data Source=sql-cpd-data-<env>-we-01.database.windows.net;Initial Catalog=sqldb-cpd-data-<env>-we-01;User Id=spappslogin;Password=P@ssw0rd123`|
|kv-cpd-apps-<env>-we-01|ConnectionStrings-StorageAccount| Secret |Connection string of the resource **stcpdappsstr<env>we01**| Eg `DefaultEndpointsProtocol=https;AccountName=stcpdappsstruatwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|
|kv-cpd-apps-<env>-we-01|Crm-CaseManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Case api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-case-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-case-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-Common-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for common dynamic connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-common-integration-test <p>Client Secret : **********</p><p> TEST - spn-crm-common-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-general-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|Crm-ProfileManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Profile api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> TEST - spn-crm-profile-management-integration-test<p>Client Secret : **********</p><p> DEV - spn-crm-profile-management-integration-dev<p>Client Secret : **********</p>||
|kv-cpd-apps-<env>-we-01|EventGridSettings-DomainKey| Secret | Access key of egd-cpd-apps-int-<env>-we-01||
|kv-cpd-apps-<env>-we-01|GraphClientSecret| Secret | Client Secret of TASMU-Portal app on Azure B2C Tenant ||
|kv-cpd-apps-<env>-we-01|ManageEventFunction-AzureADOptions-ClientSecret| Secret | Client Secret of ManageEventFunction app on Azure B2C Tenant | |
|kv-cpd-apps-<env>-we-01|NotificationFunctionSettings-SendGridApiKey| Secret | **Sendgrid API key to be provided by customer.** |
|kv-cpd-apps-<env>-we-01|NotificationSettings-AuthKey| Secret | Notification History DB Auth Secondary Key, key is retrieved from cosmos-cpd-apps-<env>-we-01||
|kv-cpd-apps-<env>-we-01|NotificationSettings-AuthToken| Secret | Notification History DB Auth Primary Key, key is retrieved from cosmos-cpd-apps-<env>-we-01||
|kv-cpd-apps-<env>-we-01|NotificationSettings-AzureADOptions-ClientSecret| Secret | Client Secret for Notification API App Registration in B2C tenant||
|kv-cpd-apps-<env>-we-01|NotificationSettings-GSMSKey| Secret | Government SMS Provider Password, key to be provided by customer.||
|kv-cpd-apps-<env>-we-01|NotificationSettings-NotificationServiceBusConnectionString| Secret | Send,Listen access policy connection string of the resource sb-cpd-apps-ntf-<env>-we-01 ||
|kv-cpd-apps-<env>-we-01|NotificationSettings-SmsApiName| Secret | Ooredoo SMS Gateway Provider API Name, key to be provided by customer.||
|kv-cpd-apps-<env>-we-01|NotificationSettings-SmsApiPassword| Secret | Ooredoo SMS Gateway Password, key to be provided by customer.||
|kv-cpd-apps-<env>-we-01|OrganisationApi-AzureADOptions-ClientSecret| Secret | Client Secret of **Central-Platform-Core-APIs** app on Azure B2C Tenant ||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AuthorizeCard-ClientSecret| Secret | @<61B6AA19-06EB-6663-BCF0-23DE48E289A0> ||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AuthorizeCard-Password| Secret |@<61B6AA19-06EB-6663-BCF0-23DE48E289A0>||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-GetPaymentPreferenceServiceURL| Secret |@<61B6AA19-06EB-6663-BCF0-23DE48E289A0>||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-TerminalPwd| Secret |@<61B6AA19-06EB-6663-BCF0-23DE48E289A0>||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-Token| Secret |@<61B6AA19-06EB-6663-BCF0-23DE48E289A0>||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-AzureAd-ClientSecret| Secret| @<61B6AA19-06EB-6663-BCF0-23DE48E289A0>||
|kv-cpd-apps-<env>-we-01|PaymentGWSettings-UpdatePaymentPreferenceServiceURL| Secret | @<61B6AA19-06EB-6663-BCF0-23DE48E289A0>|
|kv-cpd-apps-<env>-we-01|PowerBIEmbed-AzureAd-ClientSecret| Secret |@<0D90F5BE-863D-67CD-B107-FDC13EEA38B4> ||
|kv-cpd-apps-<env>-we-01|SmartParking-ADAuth-ClientSecret| Secret |Client Secret for Smart Parking APi App registration in B2C tenant||
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint| CMSBPA Self signed certificate|
|kv-cpd-apps-<env>-we-01|Cms-Api-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint|CMSAPI Self signed certificate| 