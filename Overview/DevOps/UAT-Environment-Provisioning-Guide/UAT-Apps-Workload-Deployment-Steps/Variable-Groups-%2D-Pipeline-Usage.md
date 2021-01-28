Notes:
1. Apart from the Key Vault Secrets being stored as secure variable in respective pipelines, following variables are required as well

|Variable Name| How to Retrieve | Example (UAT)| Type| Pipelines Using |
|--|--|--|--|--|
|ApplicationInsights-ConnectionString| Connection string of `appi-cpd-apps-mon-<env>-we-01` |Eg. `InstrumentationKey=984ca526-2038-4d9d-b0cf-653706512c58`|Plain Text|CD-PlatformApis-Release|
|ApplicationInsights-InstrumentationKey| Instrumentation key of `appi-cpd-apps-mon-<env>-we-01` |Eg. `984ca526-2038-4d9d-b0cf-653706512c58`|Plain Text|CD-PlatformApis-Release|
|Azure-Search-Key|Primary Admin key of resource `srch-cpd-apps-cog-<env>-we-01`||Secure|CI-APIMConfig-Master-Build|
|Bot-Directline-Key| DirectLine secret of `bot-cpd-apps-<env>-we-01` under WebAppBot Azure resource -> channels -> Direct Line -> Secret||Secure|CI-APIMConfig-Master-Build|
|ConnectionStrings-StorageAccount|Connection string of the resource stcpdglobacmwe01|Eg. `DefaultEndpointsProtocol=https;AccountName=stcpdglobacmwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|Secure|CD-PlatformApis-Release|
|LuisGeneralAppIdAr| App Id of tasmubot_ar_ar_General at (https://eu.luis.ai/) of `cog-cpd-apps-luisauth-<env>-we-01` authoring resource.|Eg. `5ce7a761-1f56-4ca7-b77a-8a69f6703b27`|Plain Text| CD-Bot-Release-Master |
|LuisGeneralAppIdEn| App Id of tasmubot_en_us_General at (https://eu.luis.ai/) of `cog-cpd-apps-luisauth-<env>-we-01` authoring resource. |Eg. `2015bee4-e5ce-45ae-9aba-234861ca005d`|Plain Text| CD-Bot-Release-Master |
|Mobile-AppCenterDroidKey| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `cb8b60ea-3a62-4bfc-9061-5fe61d915025`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-AppCenterIosKey| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `62ee3511-08ae-4fd8-9cd4-46d15ee42f1a`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-CmsSubscriptionKeyName| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> ||Secure|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-ConfigApiEndPoint| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `https://api.uat.sqcp.qa/config`||Plain TextCI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubListenConn| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> ||Secure|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubName| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `ntf-cpd-apps-str-uat-we-01`|Plain Text|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|