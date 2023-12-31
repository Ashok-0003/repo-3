[[_TOC_]]
# App Configuration Mappings
|Key Name| How to retrieve | Remarks/ Examples (UAT)|
|--|--|--|
|AdminPortal.ADAuth:Authority|Microsoft login Authority url with **B2C TenantId** **https://login.microsoftonline.com/<TenantId>/v2.0**| Eg. `https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0`  |
|AdminPortal.ADAuth:ClientId|ClientId of **spn-adminportal** app registration in B2C Tenant |Eg. `9b6a8eef-0181-4a7e-a5ee-7e0477db25ad` |
|AdminPortal.ADAuth:Domain|B2C Tenant Domain Name | Eg.`tasmucpb2cnonprod.onmicrosoft.com`|
|AdminPortal.ADAuth:Scope| SmartParking api default scope from **Smart Parking API** app registration as shown in example `https://<B2C Tenant Domain Name>/SmartParkingAPI/.default`|Eg.`https://tasmucpb2cnonprod.onmicrosoft.com/SmartParkingAPI/.default` |
|AdminPortal.ADAuth:TenantId| Directory(tenant) Id of **spn-adminportal** app registration in B2C Tenant|Eg.`24f9d756-bf0c-43e9-ad5e-2073ae2d6698` |
|AppSettings:ApiBaseUrl| Base URL for APIs end point (routing via APIM) |Eg. `https://api.<env>.sqcp.qa`|
|AppSettings:InstrumentationKey| Instrumentation Key of the resource (appi-cpd-apps-mon-<env>-we-01) | Eg. `984ca526-2038-4d9d-b0cf-653706512c58`|
|AzureSearchFunction.AzureSearchSettings:ServiceName|Search Index Name from resource **srch-cpd-apps-cog-<env>-we-01**|Eg. `srch-cpd-apps-cog-<env>-we-01.search.windows.net`|
|Bot.AppSettings:ArQnaMaker:Endpoint| Endpoint value under Keys and Endpoint section of appcog-cpd-apps-arqna-<env>-we-01 cognitive services resource  |<p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. `https://appcog-cpd-apps-arqna-<env>-we-01.cognitiveservices.azure.com/`|
|Bot.AppSettings:ArQnaMaker:EndpointKey| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-arqna-<env>-we-01 as a service and get the EndpointKey value from any knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. Authorization: EndpointKey `f35db8ce-35b4-4e9d-8511-b44554dcc80b`|
|Bot.AppSettings:ArQnaMaker:FaqKbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-arqna-<env>-we-01 as a service and get the FaqKbId value from tasmubot_FAQ_ar_ar knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. POST /knowledgebases/`bb84dae0-1c56-46bc-a02e-c872c753f3db`/generateAnswer|
|Bot.AppSettings:ArQnaMaker:Hostname| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-arqna-<env>-we-01 as a service and get the Hostname value from any knowledge base under view code.| <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. `https://appcog-cpd-apps-arqna-<env>-we-01.azurewebsites.net/`|
|Bot.AppSettings:ArQnaMaker:KbQnAkbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-arqna-<env>-we-01 as a service and get the KbQnAKbId value from tasmubot_CRMKnowledgebase_ar_ar knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. POST /knowledgebases/`30b7067d-7a83-4eb4-a2dc-46f3bd2329a8`/generateAnswer|
|Bot.AppSettings:ArQnaMaker:SourceFAQKbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-arqna-<env>-we-01 as a service and get the SourceFAQKbId value from tasmubot_Source_FAQ_ar_ar knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. POST /knowledgebases/`062bf671-d341-4c01-b652-b8a0584fcad4`/generateAnswer|
|Bot.AppSettings:CaseApiUrl| `https://api.<env>.sqcp.qa/case`|Eg. `https://api.<env>.sqcp.qa/case`|
|Bot.AppSettings:DispatchLuisAppIdAr| At [eu.luis.ai](https://eu.luis.ai/) choose authoring resource cog-cpd-apps-luisauth-<env>-we-01, then select tasmubot_ar_ar_Dispatch and under manage tab, get the App ID value. | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. `097e976b-104e-45a2-9082-2f8313f82667`|
|Bot.AppSettings:DispatchLuisAppIdEn| At [eu.luis.ai](https://eu.luis.ai/) choose authoring resource cog-cpd-apps-luisauth-<env>-we-01, then select tasmubot_en_us_Dispatch and under manage tab, get the App ID value. | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. `01381127-60b4-41c8-a184-cb4eb258ca36`|
|Bot.AppSettings:EnQnaMaker:Endpoint| Endpoint value under Keys and Endpoint section of appcog-cpd-apps-qna-<env>-we-01 cognitive services resource| <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. `https://appcog-cpd-apps-qna-<env>-we-01.cognitiveservices.azure.com/`|
|Bot.AppSettings:EnQnaMaker:EndpointKey| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-qna-<env>-we-01 as a service and get the EndpointKey value from any knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. Authorization: EndpointKey `3acd8b1c-999d-4e7d-971e-4483dd7e074f`|
|Bot.AppSettings:EnQnaMaker:FaqKbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-qna-<env>-we-01 as a service and get the FaqKbId value from tasmubot_FAQ_en_us knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. POST /knowledgebases/`f60138b7-0b5e-45d1-828f-a88ca78411f2`/generateAnswer|
|Bot.AppSettings:EnQnaMaker:Hostname| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-qna-<env>-we-01 as a service and get the Hostname value from any knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>| Eg. `https://appcog-cpd-apps-qna-<env>-we-01.azurewebsites.net/`|
|Bot.AppSettings:EnQnaMaker:KbQnAKbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-qna-<env>-we-01 as a service and get the KbQnAKbId value from tasmubot_CRMKnowledgebase_en_us knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. POST /knowledgebases/`1ce6771c-5ec6-4f65-bc23-f1070441dbb6`/generateAnswer|
|Bot.AppSettings:EnQnaMaker:SourceFAQKbId| At [qnamaker.ai](https://www.qnamaker.ai/), select appcog-cpd-apps-qna-<env>-we-01 as a service and get the SourceFAQKbId value from tasmubot_Source_FAQ_en_us knowledge base under view code.  | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. POST /knowledgebases/`08864f8b-d18b-4990-8c76-02691017ab0b`/generateAnswer|
|Bot.AppSettings:GeneralLuisAppIdAr| At [eu.luis.ai](https://eu.luis.ai/) choose authoring resource cog-cpd-apps-luisauth-<env>-we-01, then select tasmubot_ar_ar_General and under manage tab, get the App ID value. | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. `c45ab39f-b40f-4efa-887f-42776938e545`|
|Bot.AppSettings:GeneralLuisAppIdEn| At [eu.luis.ai](https://eu.luis.ai/) choose authoring resource cog-cpd-apps-luisauth-<env>-we-01, then select tasmubot_en_us_General and under manage tab, get the App ID value. | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p>Eg. `8ff9da8d-529c-4da9-8656-b76068096b1b`|
|Bot.AppSettings:KnowledgebasePortalUrl| `https://marketplace.<env>.sqcp.qa/en/support/articledetails?articleid=`|Eg. `https://marketplace.<env>.sqcp.qa/en/support/articledetails?articleid=`|
|Bot.AppSettings:Luis:AccountName|Name of the resource cog-cpd-apps-luisauth-<env>-we-01| Eg. `cog-cpd-apps-luisauth-dev-we-01`|
|Bot.AppSettings:LuisCustomEndpoint| Endpoint value under Keys and Endpoint section of cog-cpd-apps-luisrt-<env>-we-01 cognitive services resource | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg. `https://cog-cpd-apps-luisrt-<env>-we-01.cognitiveservices.azure.com/`|
|Bot.AppSettings:ProductCatalogueApiUrl| `https://api.<env>.sqcp.qa/catalogue/api`|Eg. `https://api.<env>.sqcp.qa/catalogue/api`|
|Bot.AppSettings:ResourceGroupName|Name of the resource rg-cpd-apps-cog-<env>-we-01| Eg. `rg-cpd-apps-cog-dev-we-01`|
|Bot.AppSettings:SearchApiUrl| `https://api.<env>.sqcp.qa/searchapi`|Eg. `https://api.<env>.sqcp.qa/searchapi`|
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSync:LuisTrainerUri| `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/en`|Eg. `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/en`|
|Bot.AzureQnaMakerSyncFunction:ConfigQnaSyncAr:LuisTrainerUri| `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/ar`|Eg. `https://func-cpd-apps-luistra-<env>-we-01.azurewebsites.net/api/locale/ar`|
|Bot.MenuAndCards:MenuAndCards:Cards:RequestServiceOrSupportMenuCard| [Refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps%2FApp%20Configurations%20in%20the%20Config%20Store&pageId=150&anchor=bot.menuandcards%3Amenuandcards%3Acards%3Arequestserviceorsupportmenucard) |It will be a base64 encoded of the following [JSON](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps%2FApp%20Configurations%20in%20the%20Config%20Store&pageId=150&anchor=bot.menuandcards%3Amenuandcards%3Acards%3Arequestserviceorsupportmenucard).|
|Bot.MenuAndCards:MenuAndCardsAr:Cards:RequestServiceOrSupportMenuCard| [Refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps%2FApp%20Configurations%20in%20the%20Config%20Store&pageId=150&anchor=bot.menuandcards%3Amenuandcardsar%3Acards%3Arequestserviceorsupportmenucard) |It will be a base64 encoded of the following [JSON](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki?wikiVersion=GBwikiMaster&_a=edit&pagePath=%2FOverview%2FDevOps%2FUAT%20Environment%20Provisioning%20Guide%2FUAT%20Apps%20Workload%20Deployment%20Steps%2FApp%20Configurations%20in%20the%20Config%20Store&pageId=150&anchor=bot.menuandcards%3Amenuandcardsar%3Acards%3Arequestserviceorsupportmenucard).|
|CDNSettings:TenantId|The Tenant Id|Tenant Id of azure ad associated with azure subscription|
|CDNSettings:ClientId|The Client Id|Client Id of azure ad applicationassociated with azure subscription (spn-cmsbpa-prod)|
|CDNSettings:Profile|Name of the CDN profile resource cdn-cpd-shrd-<env>-we-01|Eg. cdn-cpd-shrd-<env>-we-01|
|CDNSettings:Endpoint|Name of the CDN endpoint resource <env>-cdntasmu|Eg. <env>-cdntasmu|
|CDNSettings:ResourceGroup|Name of the resource rg-cpd-shrd-<env>-we-01|Eg. rg-cpd-shrd-<env>-we-01|
|Cms.Api:ClientApp| App Name of Azure AD app spn-cmsapi-<env>|Eg. `NONISV|TASMU|spn-cmsapi-<env>`|
|Cms.Api:ClientId|Application (client) ID of Azure AD app spn-cmsapi-<env>|Eg. 5e4456ea-6c48-414e-bf7b-904882a21f82|
|Cms.Common:Resource|Redirect URL of Azure AD app spn-cmsbpa-<env>|E.g. `https://tasmusqcp<env>.sharepoint.com`|
|Cms.Common:SourceURL|Redirect URL of Azure AD app spn-cmsbpa-<env>|E.g. `https://tasmusqcp<env>.sharepoint.com`|
|Cms.Function:ClientApp|App Name of Azure AD app spn-cmsbpa-<env>|Eg. `NONISV|TASMU|spn-cmsbpa-<env>`|
|Cms.Function:GlobalSiteUrl|URL of global site|E.g. `https://tasmusqcp<env>.sharepoint.com/sites/cms-global`|
|Cms.Function:MarketplaceSiteUrl|URL of marketplace site|E.g. `https://tasmusqcp<env>.sharepoint.com/sites/cms-marketplace`|
|Cms.Function:NotificationUrl|URL of CMS Notification Api, Notify operation|E.g. `https://api.<env>.sqcp.qa/sharepoint/Notify`|
|Cms.Function:EventGridApiUrl|URL of the event integration api|Eg. `https://api.<env>.sqcp.qa/eventintegration/messages`|
|Cms.Function:PreviewApiUrl|Marketplace preview URL|Eg. `https://marketplace.<env>.sqcp.qa/`|
|Cms.Function:SectorTermSetId|GUID of Sectors term set present in sharepoint admin center|Go to `https://tasmusqcp<env>-admin.sharepoint.com/` -> Click on Content Services in left pane -> Term Store -> Expand TASMU -> Click Sectors -> Copy the Unique Identifier|
|Cms.Function:TASMUTermGroupId|GUID of TASMU term group present in sharepoint admin center|Go to `https://tasmusqcp<env>-admin.sharepoint.com/` -> Click on Content Services in left pane -> Term Store -> Click TASMU -> Copy the Unique Identifier|
|Common.CoreApis.B2CAuth:ClientId| Client Id of Central-Platform-Core-APIs| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Common.CoreApis.B2CAuth:Domain| Domain of Central-Platform-Core-APIs| Eg: tasmucpb2cnonprod.onmicrosoft.com | 
|Common.CoreApis.B2CAuth:Instance| Instance of Central-Platform-Core-APIs| Eg: https://tasmucpb2cnonprod.b2clogin.com/tfp/ | 
|Common.CoreApis.S2SAuth:Audience| Audience of Central-Platform-Core-APIs| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Common.CoreApis.S2SAuth:Authority| Authority of Central-Platform-Core-APIs| Eg: https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0/|
|ConnectionStrings:CosmosDBEndpoint| End point for Cosmos Account|Eg. `https://cosmos-cpd-apps-str-<env>-we-01.documents.azure.com:443/`|
|ConnectionStrings:GisParkingLotsApi||Eg. `https://api.<env>.sqcp.qa/`|
|ConnectionStrings:NotificationApi| End point for notification api |Eg. `https://notification.<env>.sqcp.qa/api/Notification/`|
|ConnectionStrings:ProfileApi|End point for profile api|Eg. `https://api.<env>.sqcp.qa/profile/api/`|
|ConnectionStrings:SmartParkingApi|End point for smartparking api|Eg. `https://api.<env>.sqcp.qa/smartparking/api/`|
|Crm.CaseManagement.DynamicsSettings:Authority| Authority of App Registration - spn-crm-case-management-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|Crm.CaseManagement.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-case-management-integration-<env>| Eg: 37fd8453-e25f-4b3e-bd78-32b28328f51a|
|Crm.CaseManagement.DynamicsSettings:Resource| Url of dynamics instance for the environment - spn-crm-case-management-integration-<env>| Eg: https://tasmu-uat.crm4.dynamics.com|
|Crm.CaseManagement.DynamicsSettings:TenantId| TenantId of App Registration - spn-crm-case-management-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|Crm.Common.B2CAuth:ClientId| Client Id of Central-Platform-Core-APIs| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Crm.Common.B2CAuth:Domain| Domain of Central-Platform-Core-APIs| Eg: tasmucpb2cnonprod.onmicrosoft.com|
|Crm.Common.B2CAuth:Instance| Instance of Central-Platform-Core-APIs| Eg: https://tasmucpb2cnonprod.b2clogin.com/tfp/|
|Crm.Common.DynamicsSettings:Authority| Authority of App Registration - spn-crm-common-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|Crm.Common.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-common-integration-<env>| Eg: 9364f7ba-f249-4151-b278-c5fd3c00c5a8|
|Crm.Common.DynamicsSettings:Resource| Url of dynamics instance for the environment - spn-crm-common-integration-<env>| Eg: https://tasmu-uat.crm4.dynamics.com|
|Crm.Common.DynamicsSettings:TenantId| TenantId of App Registration - spn-crm-common-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|Crm.Common.S2SAuth:Audience| Audience of Central-Platform-Core-APIs| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|Crm.Common.S2SAuth:Authority| Authority of Central-Platform-Core-APIs| Eg: https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0/|
|Crm.ProfileManagement.DynamicsSettings:Authority| Authority of App Registration - spn-crm-profile-management-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|Crm.ProfileManagement.DynamicsSettings:ClientId| Client Id of App Registration - spn-crm-profile-management-integration-<env>| Eg: d60021f7-df14-4731-a311-83d30d2bec1b|
|Crm.ProfileManagement.DynamicsSettings:Resource| Url of dynamics instance for the environment - spn-crm-profile-management-integration-<env>| Eg: https://tasmu-uat.crm4.dynamics.com|
|Crm.ProfileManagement.DynamicsSettings:TenantId| TenantId of App Registration - spn-crm-profile-management-integration-<env>| Eg: https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355|
|EventGridSettings:DomainEndpoint|Name of the resource https://egd-cpd-apps-int-<env>-we-01.westeurope-1.eventgrid.azure.net/api/events||
|GraphB2cExtensionAppClientId|Client Id of default B2C extension app in Azure B2C tenant ||
|GraphClientId|Client Id of TASMU-Portal app in Azure B2C tenant||
|GraphTenant|Tenant Id of Azure B2C Tenant||
|ManageEventFunction.AzureADOptions:ClientId|Client Id of ManageEventFunction app registration |Eg: 11f1f420-3ce0-4f26-85f5-9cf902553e72|
|ManageEventFunction.AzureADOptions:Instance|Instance of ManageEventFunction app registration |Eg: https://login.microsoftonline.com/{0}|
|ManageEventFunction.AzureADOptions:Scope|Scope of ManageEventFunction app registration |Eg: https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default|
|ManageEventFunction.AzureADOptions:TenantId|Tenant Id of ManageEventFunction app registration |Eg: 24f9d756-bf0c-43e9-ad5e-2073ae2d6698|
|MicrosoftAppId| Microsoft App Id/ClientId of webAppBot bot-cpd-apps-<env>-dev-01 | <p>For initial deployment [refer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/123/Chatbot-Information-and-Deployment-Steps?anchor=updating-infra-repo-with-luis-and-qna-keys)</p> Eg: `2d6a26ed-4c86-4d6e-b7a6-b7cee194e5e9`|
|Mobile:AccountManagementApiEndPoint|API endpoint for accountmanagement service |Eg. `https://api.<env>.sqcp.qa/accountmanagement`|
|Mobile:AuthenticationSettings:BoPolicySignUpSignIn|AAD B2C policy for business owner signup  ||
|Mobile:AuthenticationSettings:ClientId|App registration for the **TASMU-MobileApp** in AAD B2C  | Eg: `c9e6a345-fabf-4cbc-94a5-1a94638aee51`|
|Mobile:AuthenticationSettings:PolicyChangePassword|AAD B2C policy for changing password ||
|Mobile:AuthenticationSettings:PolicyLinkAccounts|AAD B2C policy for link accounts  ||
|Mobile:AuthenticationSettings:PolicyResetPassword|AAD B2C policy for resetting password ||
|Mobile:AuthenticationSettings:PolicySignUpSignIn|AAD B2C policy for individual user signup ||
|Mobile:AuthenticationSettings:Tenant|AAD B2C tenant name ||
|Mobile:AuthorizationSettings:CentralScope,0|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,1|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,2|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,3|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,4|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,5|API scope permission required for API used ||
|Mobile:AuthorizationSettings:CentralScope,6|API scope permission required for API used ||
|Mobile:AuthzPaymentEndpoint|The URL for authorization card site |Eg. `https://account.<env>.sqcp.qa/authorizecard`|
|Mobile:BillingInfoApiEndPoint|API endpoint for billing service |Eg. `https://api.<env>.sqcp.qa/billingentityinfo`|
|Mobile:CaseApiEndPoint|API endpoint for service and support service |Eg. `https://api.<env>.sqcp.qa/case`|
|Mobile:CatalogueEndPoint|API endpoint for catalogue service |Eg. `https://api.<env>.sqcp.qa/catalogue`|
|Mobile:ChatBotUrl|The URL for TASMU Chat bot |Eg. `https://<env>-cdntasmu.azureedge.net/app/botwebchat/botchatui.html?isMobile=true&locale=`|
|Mobile:ConfigApiEndPoint|API endpoint for config service |Eg. `https://api.<env>.sqcp.qa/config`|
|Mobile:CustomerManagementApiEndPoint|API endpoint for customermanagement service |Eg. `https://api.<env>.sqcp.qa/customermanagement`|
|Mobile:DemographicApiEndPoint|API endpoint for demographic service |Eg. `https://api.<env>.sqcp.qa/demographic`|
|Mobile:EndUserLicenseAgreementLink|The URL for payment EULA ||
|Mobile:FileUploadEndpoint|The URL for file upload ||
|Mobile:InvoiceApiEndpoint|API endpoint for Invoice service |Eg. `https://api.<env>.sqcp.qa/invoice`|
|Mobile:KbApiEndPoint|API endpoint for Knowledge Base service |Eg. `https://api.<env>.sqcp.qa/knowledge`|
|Mobile:OrderApiEndPoint|API endpoint for Order service |Eg. `https://api.<env>.sqcp.qa/ordermanagement`|
|Mobile:PaymentApiEndPoint|API endpoint for Payment service |Eg. `https://api.<env>.sqcp.qa/payment`|
|Mobile:ProfileApiEndPoint|API endpoint for Profile service |Eg. `https://api.<env>.sqcp.qa/profile`|
|Mobile:SearchApiEndpoint|The URL for Azure search service |Eg. `https://api.<env>.sqcp.qa`|
|Mobile:TermsAndConditionsLink|The URL for Terms & Conditions link for payments ||
|Mobile.VideoUrl|The URL for the video in About page ||
|Mobile.MaxFileUploadSizeKB|The max file size in KB||
|Mobile.DefaultCacheTtl|The default cache time-to-live time in sec ||
|Mobile.LogLevel|The log level for application instrumentation||
|NotificationFunctionSettings:ApimRootUrl|`https://api.<env>.sqcp.qa` |Eg: `https://api.<env>.sqcp.qa`|
|NotificationFunctionSettings:FromAddress|  From Email Address for Send Grid Emails |Eg: `tasmu@sqcp.qa`|
|NotificationFunctionSettings:FromName|Name of the Sender |Eg: `TASMU `|
|NotificationFunctionSettings:NotificationHubPath|Name of Notification Hub resource - ntf-cpd-apps-str-<env>-we-01|Eg: `ntf-cpd-apps-str-uat-we-01`|
|NotificationSettings:CosmosDBEndPointUri|Notification History DB EndPoint Uri, Uri is retrieved from cosmos-cpd-apps-<env>-we-01|Eg: `https://cosmos-cpd-apps-str-<env>-we-01.documents.azure.com:443/`|
|NotificationSettings:GSMSAppID|Government SMS Gateway Provider API Name, key to be provided by customer.|Eg: `ictTEST` |
|NotificationSettings:GSMSServiceUri|Government SMS Gateway Provider Uri, key to be provided by customer. |Eg: `http://10.19.167.100/smsservice/smsservice.asmx/SMSPush`|
|NotificationSettings:Originator|Ooredoo SMS Gateway Originator Key, key to be provided by customer.|Eg: `TASMUPlatf` |
|NotificationSettings:ProfileApiUrl|TASMU Platform Profile Service API Uri, the Uri is retrieved from `https://api.<env>.sqcp.qa/profile/api/profiles` |Eg: `https://api.<env>.sqcp.qa/profile/api/profiles`|
|NotificationSettings:SmsApiName|Ooredoo SMS Gateway Provider API Name, key to be provided by customer.|Eg: `tasmu` |
|NotificationSettings.ADB2CAuth:ClientId|Client Id of Notification API App Registration in B2C tenant |Eg: `64db2dba-79c5-4b6c-84e0-696b3d1f0465` |
|NotificationSettings.ADB2CAuth:Domain|Domain of TASMU non-prod/prod B2C authentication |Eg: `tasmucpb2cnonprod.onmicrosoft.com` |
|NotificationSettings.ADB2CAuth:Instance|nstance of TASMU non-prod/prod B2C authentication |Eg: `https://login.microsoftonline.com/{0}` |
|NotificationSettings.ADB2CAuth:SignUpSignInPolicyId|Get the B2C Individual policy name from custom policies in B2C Tenant B2C_1A_Signup_Signin_<env>|Eg: `B2C_1A_Signup_Signin_TST`|
|NotificationSettings.AzureADOptions:ClientId| Client Id of Notification API App Registration in B2C tenant |Eg: `64db2dba-79c5-4b6c-84e0-696b3d1f0465` |
|NotificationSettings.AzureADOptions:Domain| Domain of TASMU non-prod/prod B2C authentication |Eg: `tasmucpb2cnonprod.onmicrosoft.com` |
|NotificationSettings.AzureADOptions:Instance| Instance of TASMU non-prod/prod B2C authentication |Eg: `https://login.microsoftonline.com/{0}` |
|NotificationSettings.AzureADOptions:Scope| Notification API App Registration Scope in B2C|Eg: `https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default`|
|NotificationSettings.AzureADOptions:TenantId|Tenant Id of B2C Tenant|Eg: `24f9d756-bf0c-43e9-ad5e-2073ae2d6698`|
|NotificationSettings.S2SAuth:Audience| ClientId of Notification Api App registration |Eg. `64db2dba-79c5-4b6c-84e0-696b3d1f0465`|
|NotificationSettings.S2SAuth:Authority| TenantId of Notification Api App registration |Eg. `https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0`|
|OrganisationApi.AzureADOptions:ClientId|Client Id of Central-Platform-Core-APIs App |Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|OrganisationApi.AzureADOptions:Scope|Scope of Central-Platform-Core-APIs App |Eg:  https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default|
|OrganisationApi.AzureADOptions:Instance|Instance of Central-Platform-Core-APIs App |Eg:  https://login.microsoftonline.com/{0}|
|OrganisationApi.AzureADOptions:TenantId|Tenant Id of Central-Platform-Core-APIs App |Eg: 24f9d756-bf0c-43e9-ad5e-2073ae2d6698|
|PaymentGWSettings:GetPaymentStatusServiceURL|Ooredoo Payment Gateway Get Payment Preference Service URL provided by customer.||
|PaymentGWSettings.ADB2CAuth:ClientId|Client Id of **Central-Platform-Core-APIs** in AD B2C App Registrations| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|PaymentGWSettings.ADB2CAuth:Domain|Domain Name of B2C Tenant |Eg: tasmucpb2cnonprod.onmicrosoft.com |
|PaymentGWSettings.ADB2CAuth:Instance|Instance of TASMU non-prod/prod B2C authentication |Eg: https://tasmucpb2cnonprod.onmicrosoft.com/tfp/ |
|PaymentGWSettings.ADB2CAuth:SignUpSignInPolicyId|Get the B2C Individual policy name from custom policies in B2C Tenant B2C_1A_Signup_Signin_<env>|Eg: B2C_1A_signup_signin |
|PaymentGWSettings.AuthorizeCard:AccessTokenURL| B2C access token URL `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token` |Eg. `https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/oauth2/v2.0/token`|
|PaymentGWSettings.AuthorizeCard:AutoPayTerminalId|unique terminal ID provided by customer for Ooredoo Payment Gateway.|Eg: TASMU-DEV1 |
|PaymentGWSettings.AuthorizeCard:PaymentGatewayAPIurl|URL of the Platform-API's|Eg: `https://api.dev.sqcp.qa/payment/api/PaymentGW` |
|PaymentGWSettings.AuthorizeCard:PaymentGatewayUrl|URL of the vistamoney|Eg: `https://test.vistamoney.info/paymentgateway-external/checkoutvista.xhtml?` |
|PaymentGWSettings.AuthorizeCard:Scope|Scope of **Central-Platform-Core-APIs** App|Eg. `https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default`|
|PaymentGWSettings.AuthorizeCard:ClientId|Client Id of **TASMU Portal** app registration in B2C tenant.|Eg: `dd0623e2-0163-4b05-82f8-ef798ff16c86` |
|PaymentGWSettings.S2SAuth:Audience|Client Id of **Central-Platform-Core-APIs** in AD B2C App Registrations| Eg: bc67474e-612b-4d7f-b75a-ac54d45f143a|
|PaymentGWSettings.S2SAuth:Authority|Authority of Payment Gateway APIs|Eg: https://login.microsoftonline.com/fa525e36-bf96-43bf-8932-79524b82ce2a/v2.0/ |
|PowerBIEmbed.AzureAd:ClientId|Client Id of **spn-powerbiembed** [app registration](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad---tasmusqcp.onmicrosoft.com)  |Eg: `07ab695f-5e5d-4e05-a5e6-645c70a8e4ff`  |
|PowerBIEmbed.AzureAd:TenantId| Tenant Id of Azure AD hosting the spn-powerbiembed app registration  |Eg: `92603419-35d1-4eb0-8427-cac731071355` |
|PowerBIEmbed.PowerBIEmbed:ScriptPath|CDN path for javascripts files `https://<env>-cdntasmu.azureedge.net/`| Eg: `https://uat-cdntasmu.azureedge.net/`|
|PowerBIEmbed.PowerBIEmbed:EnvPath|Enviroment Domain URL `https://account.<env>.sqcp.qa/powerbiembed/`| Eg: `https://account.uat.sqcp.qa/powerbiembed/`|
|SmartParking.ADB2CAuth:ClientId|Application(Client Id) of **Smart Parking API** app registration in B2C Tenant |Eg:`64db2dba-79c5-4b6c-84e0-696b3d1f0465` |
|SmartParking.ADB2CAuth:Domain|Domain Name of B2C Tenant|Eg: `tasmucpb2cnonprod.onmicrosoft.com`|
|SmartParking.ADB2CAuth:Instance|B2C login url like shown in example **https://<B2C Tenant shorthand name>.b2clogin.com**|Eg: `https://tasmucpb2cnonprod.b2clogin.com/`|
|SmartParking.ADB2CAuth:SignUpSignInPolicyId|Get the B2C Individual policy name from custom policies in B2C Tenant **B2C_1A_Signup_Signin_<env>**|Eg. `B2C_1A_Signup_Signin_TST`|
|SmartParking.ProfileApi.AzureADOptions:Authority|Microsoft login url with B2C Tenant Id **https://login.microsoftonline.com/<TenantId>/v2.0**|Eg. `https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0`|
|SmartParking.ProfileApi.AzureADOptions:ClientId|Client Id of **Central-Platform-Core-APIs** app registration|Eg: `bc67474e-612b-4d7f-b75a-ac54d45f143a`|
|SmartParking.ProfileApi.AzureADOptions:Domain|Domain Name of B2C Tenant where **Central-Platform-Core-APIs** app registration resides|Eg. `tasmucpb2cnonprod.onmicrosoft.com`|
|SmartParking.ProfileApi.AzureADOptions:Instance|Microsoft login url as shown in example |Eg. `https://login.microsoftonline.com/`|
|SmartParking.ProfileApi.AzureADOptions:Scope|Default api Scope of **Central-Platform-Core-APIs** app registration **https://<Tenant Name>/central-platform-core-apis/.default**|Eg: `https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default`|
|SmartParking.ProfileApi.AzureADOptions:TenantId|Tenant Id of B2C Tenant|Eg: `24f9d756-bf0c-43e9-ad5e-2073ae2d6698`|
|SmartParking.S2SAuth:Audience|ClientId of **Smart Parking API** App registration|Eg. `64db2dba-79c5-4b6c-84e0-696b3d1f0465`|
|SmartParking.S2SAuth:Authority|Microsoft login url with B2C Tenant Id **https://login.microsoftonline.com/<TenantId>/v2.0**|Eg. `https://login.microsoftonline.com/24f9d756-bf0c-43e9-ad5e-2073ae2d6698/v2.0`|
|SubscriptionId| Subscription Id of Azure |Eg. `d0694def-b27e-4bb7-900d-437fbeb802da`|

#Reference
## Bot.MenuAndCards:MenuAndCards:Cards:RequestServiceOrSupportMenuCard
1. Update following actions.url from the given JSON -
- "title": "Create Support Request", 
"url": `https://account.`<env>`.sqcp.qa/en/?navigation=requests/createsupportrequest`
- "title": "Status of Support Request",
            "url": `https://account.`<env>`.sqcp.qa/en/?navigation=requests`
```
{
    "type": "AdaptiveCard",
    "id": "RequestServiceOrSupportMenu",
    "body": [
        {
            "type": "Container",
            "spacing": "None",
            "items": [
                {
                    "type": "TextBlock",
                    "id": "title",
                    "spacing": "Medium",
                    "size": "Medium",
                    "weight": "Medium",
                    "text": "Please select one of the options below.",
                    "wrap": true
                }
            ]
        }
    ],
    "actions": [
        {
            "type": "Action.OpenUrl",
            "title": "Create Support Request",
            "url": "https://account.dev.sqcp.qa/en/?navigation=requests/createsupportrequest"
        },
        {
            "type": "Action.OpenUrl",
            "title": "Status of Support Request",
            "url": "https://account.dev.sqcp.qa/en/?navigation=requests"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "speak": "Request service or support Menu Card"
}
```
2. After updating the above JSON, convert it to base64 encoding and assign the value to  **Bot.MenuAndCards:MenuAndCardsAr:Cards:RequestServiceOrSupportMenuCard**.

## Bot.MenuAndCards:MenuAndCardsAr:Cards:RequestServiceOrSupportMenuCard
1. Update following actions.url from the given JSON -
- "title": " إرسال طلب الدعم",
"url": `https://account.`<env>`.sqcp.qa/ar/?navigation=requests/createsupportrequest`
- "title": " حالة طلب الدعم",
            "url": `https://account.`<env>`.sqcp.qa/ar/?navigation=requests`
```
{
    "type": "AdaptiveCard",
    "id": "RequestServiceOrSupportMenu",
    "body": [
        {
            "type": "Container",
            "spacing": "None",
            "items": [
                {
                    "type": "TextBlock",
                    "id": "title",
                    "spacing": "Medium",
                    "size": "Medium",
                    "weight": "Medium",
                    "text": "من فضلك حدد واحد من الخيارات الأسفل.",
                    "wrap": true
                }
            ]
        }
    ],
    "actions": [
        {
                                            "type": "Action.OpenUrl",
                                            "title": " إرسال طلب الدعم",
                                            "url": "https://account.dev.sqcp.qa/ar/?navigation=requests/createsupportrequest"
                                        },
        {
            "type": "Action.OpenUrl",
            "title": " حالة طلب الدعم",
            "url": "https://account.dev.sqcp.qa/ar/?navigation=requests"
        }
    ],
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "version": "1.0",
    "speak": "Request service or support Menu Card"
}
```
2. After updating the above JSON, convert it to base64 encoding and assign the value to  **Bot.MenuAndCards:MenuAndCardsAr:Cards:RequestServiceOrSupportMenuCard**.

## App Registrations
1. [AD B2C](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad-b2c) 
2. [AAD](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/138/Non-Prod-Environments?anchor=application-registrations-in-azure-ad---tasmusqcp.onmicrosoft.com)