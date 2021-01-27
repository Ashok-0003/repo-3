
|Variable Name| How to Retrieve | Example (UAT)| Pipelines Using |
|--|--|--|--|
|ApplicationInsights-ConnectionString| Connection string of `appi-cpd-apps-mon-<env>-we-01` |Eg. `InstrumentationKey=984ca526-2038-4d9d-b0cf-653706512c58`|CD-PlatformApis-Release|
|ApplicationInsights-InstrumentationKey| Instrumentation key of `appi-cpd-apps-mon-<env>-we-01` |Eg. `984ca526-2038-4d9d-b0cf-653706512c58`|CD-PlatformApis-Release|
|Azure-Search-Key|Primary Admin key of resource `srch-cpd-apps-cog-<env>-we-01`||CI-APIMConfig-Master-Build|
|Bot-Directline-Key| @<DFD5ADF8-872C-6CB0-8570-21B930BB3996> @<D654DCE5-848A-674D-A624-93B0AB87B9D1> ||CI-APIMConfig-Master-Build|
|ConnectionStrings-StorageAccount|Connection string of the resource stcpdglobacmwe01|Eg. `DefaultEndpointsProtocol=https;AccountName=stcpdglobacmwe01;AccountKey=<key>;EndpointSuffix=core.windows.net`|CD-PlatformApis-Release|
|LuisGeneralAppIdAr| @<DFD5ADF8-872C-6CB0-8570-21B930BB3996> @<D654DCE5-848A-674D-A624-93B0AB87B9D1>  |Eg. `5ce7a761-1f56-4ca7-b77a-8a69f6703b27`||
|LuisGeneralAppIdEn| @<DFD5ADF8-872C-6CB0-8570-21B930BB3996> @<D654DCE5-848A-674D-A624-93B0AB87B9D1>  |Eg. `2015bee4-e5ce-45ae-9aba-234861ca005d`||
|Mobile-AppCenterDroidKey| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `cb8b60ea-3a62-4bfc-9061-5fe61d915025`|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-AppCenterIosKey| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `62ee3511-08ae-4fd8-9cd4-46d15ee42f1a`|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-CmsSubscriptionKeyName| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> ||CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-ConfigApiEndPoint| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `https://api.uat.sqcp.qa/config`|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubListenConn| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> ||CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|
|Mobile-NotificationHubName| @<0D4CAFB9-9E9F-6002-8DB9-5046CBB7EA0C> |Eg. `ntf-cpd-apps-str-uat-we-01`|CI-MobileApps-Android-Build, CI-MobileApps-iOS-Build|