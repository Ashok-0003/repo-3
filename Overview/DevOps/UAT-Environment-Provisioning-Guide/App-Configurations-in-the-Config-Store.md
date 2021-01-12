
|Key Name| How to retrieve | Remarks |  |
|--|--|--|--|
|Cms.Api:ClientCertificate|Self signed certificate||
|Cms.Function:ClientCertificate|Self signed certificate||
|Cms.Function:NotificationUrl| Default(Function Key) Function URL of notify function in func-cpd-apps-intntf-<env>-we-01|||
|Cms.Function:ServiceBusConnectionString| Send,Listen access policy connection string of the resource sb-cpd-apps-int-<env>-we-01||
|CDNSettings:StorageAccount| Connection string of the resource stcpdshrd<env>we01||
|Cms.Common:Resource|Redirect URL of Azure AD app spn-cmsbpa-<env>||
|Cms.Common:SourceURL|Redirect URL of Azure AD app spn-cmsbpa-<env>||
|Cms.Common:TenantID|Directory (tenant) ID of Azure AD App spn-cmsbpa-<env>||
|Cms.Function:ChangeLogConfigList|ChangeLog list name at global site|If list name is "ChangeLog" then value should be "ChangeLog"|
|Cms.Function:ClientApp|App Name of Azure AD app spn-cmsbpa-<env>||
|Cms.Function:ClientId|Application (client) ID of Azure AD app spn-cmsbpa-<env>||
|Cms.Function:GlobalConfigList|Configuartion list name at global site|If list name is "Configuration" then value should be "Configuration"|
|Cms.Function:GlobalSiteUrl|URL of global site||
|Cms.Function:MarketplaceSiteUrl|URL of marketplace site||
|Cms.Function:EventGridApiUrl|URL of the event integration api||
|Cms.Function:PreviewApiUrl|Marketplace preview URL||
|Cms.Function:TASMUTermGroupId|GUID of TASMU term group present in sharepoint admin center|Go to https://tasmusqcp<env>-admin.sharepoint.com/ -> Click on Content Services in left pane -> Term Store -> Click TASMU -> Copy the Unique Identifier|
|Cms.Function:SectorTermSetId|GUID of Sectors term set present in sharepoint admin center|Go to https://tasmusqcp<env>-admin.sharepoint.com/ -> Click on Content Services in left pane -> Term Store -> Expand TASMU -> Click Sectors -> Copy the Unique Identifier|
|CDNSettings:Profile|Name of the CDN profile resource cdn-cpd-shrd-<env>-we-01||
|CDNSettings:Endpoint|Name of the CDN endpoint resource <env>-cdntasmu||
|CDNSettings:Container|The storage blob container linked to CDN endpoint||
|CDNSettings:ResourceGroup|Name of the resource rg-cpd-shrd-<env>-we-01||
|AppSettings:TerminalId|Name of the resource TASMU-<env>||
|Bot.AppSettings:Luis:AccountName|Name of the resource cog-cpd-apps-luisauth-<env>-we-01||
|Bot.AppSettings:QnaMaker:0:Endpoint|Name of the resource https://appcog-cpd-apps-qna-<env>-we-01.cognitiveservices.azure.com/||
|Bot.AppSettings:ResourceGroupName|Name of the resource rg-cpd-apps-cog-<env>-we-01||
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

