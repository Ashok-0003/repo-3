
|Key Name| How to retrieve | Remarks/ Examples (UAT)|
|--|--|--|
|AdminPortal.ADAuth:Authority| | |
|AdminPortal.ADAuth:ClientId| | |
|AdminPortal.ADAuth:Domain| | |
|AdminPortal.ADAuth:Scope| | |
|AdminPortal.ADAuth:TenantId| | |
|AppSettings:ApiBaseUrl| |Eg. `https://api.<env>.sqcp.qa`|
|AppSettings:InstrumentationKey| | |
|AppSettings:TerminalId|Name of the resource TASMU-<env>||
|AzureSearchFunction.AzureSearchSettings:ServiceName| |Eg. srch-cpd-apps-cog-<env>-we-01.search.windows.net|
|Bot.AppSettings:ArQnaMaker:Endpoint||Eg. `https://appcog-cpd-apps-arqna-<env>-we-01.cognitiveservices.azure.com/`|
|Bot.AppSettings:ArQnaMaker:Hostname||Eg. `https://appcog-cpd-apps-arqna-<env>-we-01.azurewebsites.net/`|
|Bot.AppSettings:CaseApiUrl||Eg. `https://api.<env>.sqcp.qa/case`|
|Bot.AppSettings:Luis:AccountName|Name of the resource cog-cpd-apps-luisauth-<env>-we-01||
|Bot.AppSettings:EnQnaMaker:Endpoint|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AppSettings:KnowledgebasePortalUrl||Eg. `https://marketplace.prd.sqcp.qa/en/support/articledetails?articleid=`|
|Bot.AppSettings:LuisCustomEndpoint||Eg. `https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/`|
|Bot.AppSettings:ProductCatalogueApiUrl||Eg. `https://api.<env>.sqcp.qa/catalogue/api`|
|Bot.AppSettings:ResourceGroupName|Name of the resource rg-cpd-apps-cog-<env>-we-01||
|Bot.AppSettings:SearchApiUrl||Eg. `https://api.<env>.sqcp.qa/searchapi`|
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSync:DestinationCopyQna:LuisTrainerUri||Eg. `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/en`|
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:DestinationCopyQna:LuisTrainerUri||Eg. `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/ar`|
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:DestinationCopyQna:Endpoint|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:KbQna:Endpoint|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSync:LuisTrainerUri|Name of the resource https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/en||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:DestinationCopyQna:Endpoint|Name of the resource https://appcog-cpd-apps-arqna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:KbQna:Endpoint|Name of the resource https://appcog-cpd-apps-arqna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:LuisTrainerUri|Name of the resource https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/ar||
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:SourceCopyQna:Endpoint|Name of the resource https://appcog-cpd-apps-arqna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.CognitiveModels:CognitiveModels:Ar-ar:DispatchModel:CustomEndpoint|Name of the resource https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/||
|Bot.CognitiveModels:CognitiveModels:Ar-ar:Knowledgebases:0:Hostname|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.azurewebsites.net/||
|Bot.CognitiveModels:CognitiveModels:Ar-ar:Knowledgebases:1:Hostname|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.azurewebsites.net/||
|Bot.CognitiveModels:CognitiveModels:Ar-ar:LanguageModels:0:CustomEndpoint|Name of the resource https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/||
|Bot.CognitiveModels:CognitiveModels:En-us:DispatchModel:CustomEndpoint|Name of the resource https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/||
|Bot.CognitiveModels:CognitiveModels:En-us:Knowledgebases:0:Hostname|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.azurewebsites.net/||
|Bot.CognitiveModels:CognitiveModels:En-us:Knowledgebases:1:Hostname|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.azurewebsites.net/||
|Bot.CognitiveModels:CognitiveModels:En-us:LanguageModels:0:CustomEndpoint|Name of the resource https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/||
|CDNSettings:TenantId|The Tenant Id|Tenant Id of azure ad associated with azure subscription|
|CDNSettings:ClientId|The Client Id|Client Id of **spn-cmsbpa-dev**|
|CDNSettings:Profile|Name of the CDN profile resource cdn-cpd-shrd-<env>-we-01||
|CDNSettings:Endpoint|Name of the CDN endpoint resource <env>-cdntasmu||
|CDNSettings:ResourceGroup|Name of the resource rg-cpd-shrd-<env>-we-01||
|Cms.Common:Resource|Redirect URL of Azure AD app spn-cmsbpa-<env>|E.g. `https://tasmusqcp<env>.sharepoint.com`|
|Cms.Common:SourceURL|Redirect URL of Azure AD app spn-cmsbpa-<env>|E.g. `https://tasmusqcp<env>.sharepoint.com`|
|Cms.Function:ClientApp|App Name of Azure AD app spn-cmsbpa-<env>||
|Cms.Function:GlobalSiteUrl|URL of global site|E.g. `https://tasmusqcp<env>.sharepoint.com/sites/cms-global`|
|Cms.Function:MarketplaceSiteUrl|URL of marketplace site|E.g. `https://tasmusqcp<env>.sharepoint.com/sites/cms-marketplace`|
|Cms.Function:EventGridApiUrl|URL of the event integration api||
|Cms.Function:PreviewApiUrl|Marketplace preview URL||
|Cms.Function:TASMUTermGroupId|GUID of TASMU term group present in sharepoint admin center|Go to `https://tasmusqcp<env>-admin.sharepoint.com/` -> Click on Content Services in left pane -> Term Store -> Click TASMU -> Copy the Unique Identifier|
|Cms.Function:SectorTermSetId|GUID of Sectors term set present in sharepoint admin center|Go to `https://tasmusqcp<env>-admin.sharepoint.com/` -> Click on Content Services in left pane -> Term Store -> Expand TASMU -> Click Sectors -> Copy the Unique Identifier|
|Cms.Function.SupportedHtmlTags|List of HTML tags support for rich text||
|Common.CoreApis.B2CAuth:ClientId| Client Id of TASMU non prod B2C authentication| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Common.CoreApis.S2SAuth:ClientId| Client Id of TASMU non prod JWT authentication| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|ConnectionStrings:CosmosDBEndpoint||Eg. `https://cosmos-cpd-apps-str-<env>-we-01.documents.azure.com:443/`|
|ConnectionStrings:GisParkingLotsApi||Eg. `https://api.<env>.sqcp.qa/`|
|ConnectionStrings:NotificationApi||Eg. `https://api.<env>.sqcp.qa/notification/api/Notification/`|
|ConnectionStrings:ProfileApi||Eg. `https://api.<env>.sqcp.qa/profile/api/`|
|ConnectionStrings:SmartParkingApi||Eg. `https://api.<env>.sqcp.qa/smartparking/api/`|
|Crm.CaseManagement.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-case-management-integration-<env>| Eg: 37fd8453-e25f-4b3e-bd78-32b28328f51a|
|Crm.Common.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-common-integration-<env>| Eg: 9364f7ba-f249-4151-b278-c5fd3c00c5a8|
|Crm.ProfileManagement.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-profile-management-integration-<env>| Eg: d60021f7-df14-4731-a311-83d30d2bec1b|
|Crm.Common.B2CAuth:ClientId| Client Id of TASMU non prod B2C authentication| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Crm.Common.S2SAuth:ClientId| Client Id of TASMU non prod JWT authentication| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|EventGridSettings:DomainEndpoint|Name of the resource https://egd-cpd-apps-int-<env>-we-01.westeurope-1.eventgrid.azure.net/api/events||
|ManageEventFunction.AzureADOptions:ClientId|Client Id of |Eg:|
|ManageEventFunction.AzureADOptions:Instance|Instance of |Eg:|
|ManageEventFunction.AzureADOptions:Scope|Scope of |Eg:|
|ManageEventFunction.AzureADOptions:TenantId|Tenant Id of |Eg:|
|Mobile:AccountManagementApiEndPoint||Eg. `https://api.<env>.sqcp.qa/accountmanagement`|
|Mobile:AuthzPaymentEndpoint||Eg. `https://account.<env>.sqcp.qa/authorizecard`|
|Mobile:BillingInfoApiEndPoint||Eg. `https://api.<env>.sqcp.qa/billingentityinfo`|
|Mobile:CaseApiEndPoint||Eg. `https://api.<env>.sqcp.qa/case`|
|Mobile:CatalogueEndPoint||Eg. `https://api.<env>.sqcp.qa/catalogue`|
|Mobile:ChatBotUrl||Eg. `https://<env>-cdntasmu.azureedge.net/app/botwebchat/botchatui.html?isMobile=true&locale=`|
|Mobile:ConfigApiEndPoint||Eg. `https://api.<env>.sqcp.qa/config`|
|Mobile:CustomerManagementApiEndPoint||Eg. `https://api.<env>.sqcp.qa/customermanagement`|
|Mobile:DemographicApiEndPoint||Eg. `https://api.<env>.sqcp.qa/demographic`|
|Mobile:InvoiceApiEndpoint||Eg. `https://api.<env>.sqcp.qa/invoice`|
|Mobile:KbApiEndPoint||Eg. `https://api.<env>.sqcp.qa/knowledge`|
|Mobile:OrderApiEndPoint||Eg. `https://api.<env>.sqcp.qa/ordermanagement`|
|Mobile:PaymentApiEndPoint||Eg. `https://api.<env>.sqcp.qa/payment`|
|Mobile:ProfileApiEndPoint||Eg. `https://api.<env>.sqcp.qa/profile`|
|Mobile:SearchApiEndpoint||Eg. `https://api.<env>.sqcp.qa`|
|NotificationFunctionSettings:ApimRootUrl||Eg. `https://api.<env>.sqcp.qa`|
|NotificationFunctionSettings:NotificationHubPath|Name of Notification Hub resource - ntf-cpd-apps-str-<env>-we-01||
|NotificationSettings:CosmosDBEndPointUri||Eg. `https://cosmos-cpd-apps-str-<env>-we-01.documents.azure.com:443/`|
|NotificationSettings:ProfileApiUrl||Eg. `https://api.<env>.sqcp.qa/profile/api/profiles`|
|NotificationSettings.ADB2CAuth:ClientId|Client Id of |Eg: |
|NotificationSettings.ADB2CAuth:Domain|Domain of |Eg: |
|NotificationSettings.ADB2CAuth:Instance|Instance of |Eg: |
|NotificationSettings.AzureADOptions:ClientId|Client Id of |Eg: |
|NotificationSettings.AzureADOptions:Domain|Domain of |Eg: |
|NotificationSettings.AzureADOptions:Instance|Instance of |Eg: |
|NotificationSettings.AzureADOptions:TenantId|Tenant Id of |Eg: |
|OrganisationApi.AzureADOptions:ClientId|Client Id of |Eg: |
|OrganisationApi.AzureADOptions:Scope|Scope of |Eg: |
|OrganisationApi.AzureADOptions:Instance|Instance of |Eg: |
|OrganisationApi.AzureADOptions:TenantId|Tenant Id of |Eg: |
|PaymentGWSettings.ADB2CAuth:ClientId|Client Id of |Eg: |
|PaymentGWSettings.ADB2CAuth:Domain|Domain of |Eg: |
|PaymentGWSettings.ADB2CAuth:Instance|Instance of |Eg: |
|PowerBIEmbed.AzureAd:ClientId|Client Id of |Eg: |
|PowerBIEmbed.AzureAd:TenantId|Tenant Id of |Eg: |
|SmartParking.ADB2CAuth:ClientId|Client Id of |Eg: |
|SmartParking.ADB2CAuth:Domain|Domain of |Eg: |
|SmartParking.ADB2CAuth:Instance|Instance of |Eg: |
|SmartParking.ProfileApi.AzureADOptions:ClientId|Client Id of |Eg: |
|SmartParking.ProfileApi.AzureADOptions:Scope|Scope of |Eg: |
|SmartParking.ProfileApi.AzureADOptions:TenantId|Tenant Id of |Eg: |