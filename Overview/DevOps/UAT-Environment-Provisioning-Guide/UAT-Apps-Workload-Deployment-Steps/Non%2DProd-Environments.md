[[_TOC_]]
# Azure AD B2C Instance
Tenant Name: tasmucpb2cnonprod.onmicrosoft.com
Tenant ID: 24f9d756-bf0c-43e9-ad5e-2073ae2d6698

# Detailed AD B2C Setup
Refer the document uploaded on [Ooredoo Sharepoint](https://ooredooonline.sharepoint.com/:w:/s/TASMU-CentralPlatformPMO/EdIKRGu6E1VGnA-naCTSBXQBjgdtCiT9C6n5E9rehxUWmw?e=ZSX2Yf)

# Application Registrations in Azure AD B2C

|SL| App Registrations  | 
|--|--|
| 1 | IdentityExperienceFramework<p>clientid:9cdd7fad-14bf-46e0-8776-d553f1ad3402</p> | | |
| 2 | ProxyIdentityExperienceFramework <p>clientid:ead1b126-6f19-4fe0-b11c-b976c010cbf5</p>|
| 3 |b2c-extensions-app. Do not modify. Used by AADB2C for storing user data. <p>clientid:7a966e81-c9d4-4a5e-b170-d37c45e282bd</p>|
| 4 | <p>Central-Platform-Core-APIs</p><p>clientid: bc67474e-612b-4d7f-b75a-ac54d45f143a</p><p>clientsecret: ~-P5-4IVO44Xvqau5.6XH0L~B9Vcgz473m</p><p>Scopes:</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Subscription.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Subscription.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Review.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/FieldService.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/FieldService.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/ServiceRequest.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/ServiceRequest.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Organisation.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Organisation.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Case.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Case.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Profile.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Profile.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/File.Read.All</p>| | 
| 5 | TASMU-Portal <p>clientid: dd0623e2-0163-4b05-82f8-ef798ff16c86</p>  Secret jNEGx~YBG.PUZj9969BvjZ7B~ZEL5a-W5y|
| 6 | <p>TASMU-MobileApp </p><p>clientid: c9e6a345-fabf-4cbc-94a5-1a94638aee51</p><p>Scopes:</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Profile.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Profile.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Subscription.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Subscription.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Case.Read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Case.Write</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/Review.Write</p>|
| 7 | <p>Dynamics365Client</p> <p>clientid: 315614d7-eae9-4021-8836-640f4d3a9583</p><p>clientsecret: aYgcrfnV1xVsfVP~.94J3lctl.fR7f~jRM</p>|
| 8 | Notification Service API <p>clientid: 016c0e73-6713-4fe9-a18e-b5f1be83de92</p><p>clientsecret: Xcs0~4IIgudrQKNJ3rtDSs_X5j-6f~.X~8</p>|
| 9 | Smart Parking API ?? <p>clientid: 64db2dba-79c5-4b6c-84e0-696b3d1f0465</p><p>clientsecret: jgUnyX7VziON-~59iM_mL-F6J~MDMlzRtS</p><p>scope: https://tasmucpb2cnonprod.onmicrosoft.com/SmartParkingAPI/read</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/SmartParkingAPI/user_impersonation</p>|
|10 | spn-adminportal <p>clientid: 9b6a8eef-0181-4a7e-a5ee-7e0477db25ad</p><p>clientsecret: 619nB86VE4~wds-Kir-4H~vSVHExz-8~Lo</p>|
|11 | ManageEventFunction<p>clientid: 11f1f420-3ce0-4f26-85f5-9cf902553e72</p><p>clientsecret: nHYgb4zKoOfQ8GuDK6l3_qe9.rU--6eRte</p><p>scope: https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default</p>|
|12 | ITSM Non Prod<p>clientid: ce633c1d-d8b4-4381-b68a-1f7d0851250f</p><p>clientsecret: WnIaXQ~IT~P.O3CyjZNmwnj42vC2FoK_B7</p><p>scope: https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default</p>|
|13|6DClient <p>Client ID: 1e5dfced-126a-4009-8479-21bfc4e078c1</p><p>Client Secret : cK4XfnAo3a..~If43-91m6.ui_Gb2Qbu1m</p><p> Refer the AD B2C for the API Permissions configured </p>|
|14|SQCPMonitoring <p>Client ID: ca9d5b7b-8193-4200-bb4b-a56d9b7e32d3</p><p>Client Secret : tlbu57fpi-AKxt3Z.e-L5-T5-lj3~GRhgi</p>|
| 15 | <p>AuthorizeCard</p><p>clientid: dd0623e2-0163-4b05-82f8-ef798ff16c86</p><p>clientsecret: JBJGh02_5JL9_Ia-ea~C1-vBTuPDB0f1FC</p><p>Scopes:</p><p>https://tasmucpb2cnonprod.onmicrosoft.com/central-platform-core-apis/.default| | 

# Azure AD Instance
Tenant Name - tasmusqcp.onmicrosoft.com
Tenant Id - 92603419-35d1-4eb0-8427-cac731071355
# Application Registrations in Azure AD - tasmusqcp.onmicrosoft.com

|SL| App Registrations |Environment |
|--|--|--|
1|<p><p>spn-crm-common-integration-test</p>Client ID: 9364f7ba-f249-4151-b278-c5fd3c00c5a8</p><p>Client Secret : **********</p><p><p>|Test
2|<p><p>spn-crm-profile-management-integration-test</p>Client ID: d60021f7-df14-4731-a311-83d30d2bec1b</p><p>Client Secret : **********</p><p><p>|Test
3|<p><p>spn-crm-case-management-integration-test</p>Client ID: 37fd8453-e25f-4b3e-bd78-32b28328f51a</p><p>Client Secret : **********</p><p><p>|Test
4|<p><p>spn-crm-general-integration-dev</p>Client ID: d99b1bc8-c4b4-4165-821c-bfa088255bfa</p><p>Client Secret : **********</p><p><p>|Dev
5|<p><p>spn-crm-profile-management-integration-dev</p>Client ID: 339cd370-6762-4b24-be2e-35ffa8d3bcc4</p><p>Client Secret : **********</p><p><p>|Dev
6|<p><p>spn-crm-case-management-integration-dev</p>Client ID: 28832e23-19ed-48b8-aaff-4979519394df</p><p>Client Secret : **********</p><p><p>|Dev
7|<p><p>spn-crm-common-integration-test</p>Client ID: 9364f7ba-f249-4151-b278-c5fd3c00c5a8</p><p>Client Secret : **********</p><p><p>|UAT
8|<p><p>spn-crm-profile-management-integration-test</p>Client ID: d60021f7-df14-4731-a311-83d30d2bec1b</p><p>Client Secret : **********</p><p><p>|UAT
9|<p><p>spn-crm-case-management-integration-test</p>Client ID: 37fd8453-e25f-4b3e-bd78-32b28328f51a</p><p>Client Secret : **********</p><p><p>|UAT
10|<p><p>spn-cmsbpa-dev</p>Client ID: 18de3da3-ecfa-4b26-b819-f6bf366f0265</p><p>Certificate</p><p><p>|Dev
11|<p><p>spn-cmsapi-dev</p>Client ID: 8b3a1cb0-c080-4a28-ae3e-3de3de56549c</p><p>Certificate</p><p><p>|Dev
12|<p><p>spn-cmsbpa-tst</p>Client ID: f822b95e-e7ae-4b4c-945d-a2791b96c43a</p><p>Certificate</p><p><p>|Test
13|<p><p>spn-cmsapi-tst</p>Client ID: 570a1b9e-f0e6-43da-a8af-aa8f7f31044e</p><p>Certificate</p><p><p>|Test
14|<p><p>spn-cmsbpa-uat</p>Client ID: 5cff9256-4cc7-4b39-92a2-e48926e22d7c</p><p>Certificate</p><p><p>|UAT
15|<p><p>spn-cmsapi-uat</p>Client ID: 5e4456ea-6c48-414e-bf7b-904882a21f82</p><p>Certificate</p><p><p>|UAT
16|<p><p>spn-bot-dev</p>Client ID: 2d6a26ed-4c86-4d6e-b7a6-b7cee194e5e9</p><p>Client Secret : **********</p><p><p>|Dev
17|<p><p>spn-bot-tst</p>Client ID: 85100d91-3748-446e-b434-a2e5b842c667</p><p>Client Secret : **********</p><p><p>|Test
18|<p><p>spn-bot-sbx</p>Client ID: 291f394b-1c27-4ddd-b64c-cfa5f65ecea7</p><p>Client Secret : **********</p><p><p>|SBX
19|<p><p>spn-bot-tra</p>Client ID: 7c42dfb0-b532-4c89-a3cf-9a8a7578bd03</p><p>Client Secret : **********</p><p><p>|TRA
20|<p><p>spn-bot-uat</p>Client ID: 64d794aa-a017-4fe2-a793-fa841ebed766</p><p>Client Secret : **********</p><p><p>|UAT
21|<p><p>spn-powerbiembed</p>Client ID: 07ab695f-5e5d-4e05-a5e6-645c70a8e4ff</p><p>Client Secret : **********</p><p><p>|DEV, TST, TRA, UAT
22|<p><p>spn-armapi-reader-npd</p>Client ID: c00ce23b-b4cd-4164-9735-3c63381f9441</p><p>Client Secret : **********</p><p><p>|DEV, TST, TRA, UAT, SBX

**For more details on CMS Azure AD apps please refer** : [*CMS Azure AD apps*](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/153/CMS-Azure-AD-apps) 
# Environment URLs
## Development Environment
|SL| Portal / App | URL |  Remarks  |
|--|--|--|--|
| 1 | API Access URL  | https://api.dev.sqcp.qa | Base URL for all API calls  |
| 2 | Marketplace Portal (B2B)  | https://marketplace.dev.sqcp.qa  |  |
| 3 | Smart Services Portal (B2C)  | https://mytasmu.dev.sqcp.qa  |  |
| 4 | Developer Portal | https://developer.dev.sqcp.qa |  |
| 5 | Open Data Portal | https://opendata.dev.sqcp.qa |  |
| 6 | SQCP Admin Portal| https://cpadmin.dev.sqcp.qa | | |
| 7 | Dynamics 365 Instance|https://tasmu-dev2.crm4.dynamics.com| | |
| 8 | Office 365 Instance/Tenant | | | |
| 9 | CDN URL |https://dev-cdntasmu.azureedge.net | | | |
| 10 | Authorizecard URL |https://account.dev.sqcp.qa/authorizecard | | | |

## Test Environment

|SL| Portal / App | URL | Remarks  |
|--|--|--|--|
| 1 | API Access URL  | https://api.tst.sqcp.qa | Base URL for all API calls  |
| 2 | Marketplace Portal (B2B)  | https://marketplace.tst.sqcp.qa  |  |
| 3 | Smart Services Portal (B2C)  | https://mytasmu.tst.sqcp.qa  |  |
| 4 | Developer Portal | https://developer.tst.sqcp.qa |  |
| 5 | Open Data Portal | https://opendata.tst.sqcp.qa |  |
| 6 | SQCP Admin Portal| https://cpadmin.tst.sqcp.qa | | |
| 7 | Dynamics 365 Instance|https://tasmu-test.crm4.dynamics.com | | |
| 8 | Office 365 Instance/Tenant | | | |
| 9 | CDN URL |https://tst-cdntasmu.azureedge.net | | | |
| 10 | Authorizecard URL |https://account.tst.sqcp.qa/authorizecard | | | |

## Training Environment

|SL| Portal / App | URL | Remarks  |
|--|--|--|--|
| 1 | API Access URL  | https://api.trn.sqcp.qa | Base URL for all API calls  |
| 2 | Marketplace Portal (B2B)  | https://marketplace.trn.sqcp.qa  |  |
| 3 | Smart Services Portal (B2C)  | https://mytasmu.trn.sqcp.qa  |  |
| 4 | Developer Portal | https://developer.trn.sqcp.qa |  |
| 5 | Open Data Portal | https://opendata.trn.sqcp.qa |  |
| 6 | SQCP Admin Portal| https://cpadmin.trn.sqcp.qa | | |
| 7 | Dynamics 365 Instance|https://tasmu-uat.crm4.dynamics.com | | |
| 8 | Office 365 Instance/Tenant | | | |
| 9 | CDN URL |https://trn-cdntasmu.azureedge.net | | | |

## UAT Environment

|SL| Portal / App | URL | Remarks  |
|--|--|--|--|
| 1 | API Access URL  | https://api.uat.sqcp.qa | Base URL for all API calls  |
| 2 | Marketplace Portal (B2B)  | https://marketplace.uat.sqcp.qa  |  |
| 3 | Smart Services Portal (B2C)  | https://mytasmu.uat.sqcp.qa  |  |
| 4 | Developer Portal | https://developer.uat.sqcp.qa |  |
| 5 | Open Data Portal | https://opendata.uat.sqcp.qa |  |
| 6 | SQCP Admin Portal| https://cpadmin.uat.sqcp.qa | | |
| 7 | Dynamics 365 Instance|https://tasmu-uat.crm4.dynamics.com | | |
| 8 | Office 365 Instance/Tenant | | | |
| 9 | CDN URL |https://uat-cdntasmu.azureedge.net | | | |
| 10 | CMS URL |https://tasmusqcpuat.sharepoint.com/sites/cms-marketplace | | | |
| 11 | CMS URL2 |https://tasmusqcpuat.sharepoint.com/sites/cms-global | | | |
| 12 | Authorizecard URL |https://account.uat.sqcp.qa/authorizecard | | | |