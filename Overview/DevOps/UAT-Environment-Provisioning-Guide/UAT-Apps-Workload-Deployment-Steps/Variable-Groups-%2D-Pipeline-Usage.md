Notes:
1. Apart from the Key Vault Secrets being stored as secure variable in respective pipelines, following variables are required as well

|Variable Name| How to Retrieve | Example (UAT)| Type| Pipelines Using |
|--|--|--|--|--|
|ApplicationInsights-ConnectionString| Connection string of `appi-<sub>-apps-mon-<env>-we-01` |Eg. `InstrumentationKey=984ca526-2038-4d9d-b0cf-653706512c58`|Plain Text|CD-PlatformApis-Release|
|ApplicationInsights-InstrumentationKey| Instrumentation key of `appi-<sub>-apps-mon-<env>-we-01` |Eg. `984ca526-2038-4d9d-b0cf-653706512c58`|Plain Text|CD-PlatformApis-Release|
|ConnectionStrings-StorageAccount|Connection string of the resource `st<sub>appsstr<env>we01`|Eg. `DefaultEndpointsProtocol=https;AccountName=stcpdappsstruatwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|Secure|CD-PlatformApis-Release|
|ConnectionStrings-IntegrationServiceBus| Connection string of SAS policy (RootManageSharedAccessKey) of resource `sb-<sub>-apps-int-<env>-we-01` |Eg. `Endpoint=sb://sb-cpd-apps-int-uat-we-01.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=<key>` |Secure|CD-PlatformApis-Release|
|ConnectionStrings-Redis| Primary connection string of Redis instance `redis-<sub>-apps-str-<env>-we-01` |Eg. `redis-<sub>-apps-str-<env>-we-01.redis.cache.windows.net:6380,password=undefined,ssl=True,abortConnect=False`| | |
|NotificationSettings-NotificationServiceBusConnectionString|Connection string of SAS policy (RootManageSharedAccessKey) of resource `sb-<sub>-apps-strntf-<env>-we-01` | Eg. `Endpoint=sb://sb-cpd-apps-strntf-uat-we-01.servicebus.windows.net/;SharedAccessKeyName=RootManageSharedAccessKey;SharedAccessKey=<key>` | Secure|CD-PlatformApis-Release|
|Azure-Search-Key|Primary Admin key of resource `srch-<sub>-apps-cog-<env>-we-01`||Secure|CI-APIMConfig-Master-Build|
|Bot-Directline-Key| DirectLine secret of `bot-<sub>-apps-<env>-we-01` under WebAppBot Azure resource -> channels -> Direct Line -> Secret||Secure|CI-APIMConfig-Master-Build|
|CMS-API-CertificatePassword|Password of `CMS-CMSAPI-<env>.pfx` file.||Secure|CI-KeyVault-Master-Build, CD-KeyVaultSecrets-Master-Release|
|LuisGeneralAppIdAr| App Id of tasmubot_ar_ar_General at (https://eu.luis.ai/) of `cog-<sub>-apps-luisauth-<env>-we-01` authoring resource.|Eg. `5ce7a761-1f56-4ca7-b77a-8a69f6703b27`|Plain Text| CD-Bot-Release-Master |
|LuisGeneralAppIdEn| App Id of tasmubot_en_us_General at (https://eu.luis.ai/) of `cog-<sub>-apps-luisauth-<env>-we-01` authoring resource. |Eg. `2015bee4-e5ce-45ae-9aba-234861ca005d`|Plain Text| CD-Bot-Release-Master |
|Mobile-AppCenterDroidKey|App secret for TASMU Android App in MS App center  |Eg. `cb8b60ea-3a62-4bfc-9061-5fe61d915025`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-AppCenterIosKey| App secret for TASMU iOS App in MS App center |Eg. `62ee3511-08ae-4fd8-9cd4-46d15ee42f1a`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-CmsSubscriptionKeyName| APIM Subscription key for CMS Content API ||Secure|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-ConfigApiEndPoint| API endpoint for Config API |Eg. `https://api.uat.sqcp.qa/config`||Plain TextCI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubListenConn| Listen Access connection string of Azure Notification hub `ntfns-cpd-apps-str-uat-we-01` ||Secure|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubName| Name of the Azure Notification hub that the mobile app integrated. |Eg. `ntf-cpd-apps-str-uat-we-01`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-Msal| The mobile app registration id (clientId) in AAD B2C used for MSAL operations. |Eg. `msalg-u-i-d`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-ApiKey| The key for Google map used in the location service |Eg. `AIzaSyAcn9GXu6D4VeUWgYMkYfNvKwCTT634-A0`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|BPM-APIM-Password| BPM APIM Password |
|NGIS-App-Token| NGIS App Token - To be obtained from NGIS team. Initial ref. to apiservicePolicy.xml in "NGIS Infra" for resp. env.||
