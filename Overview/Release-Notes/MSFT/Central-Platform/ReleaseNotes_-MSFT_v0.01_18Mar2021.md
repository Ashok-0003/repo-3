[ReleaseNotes_ MSFT_v0.01_18Mar2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_18Mar2021-a9f27b95-0a80-4924-aa95-01571f5aa39f.docx)

Contents

1	🔧What’s New	2
2	🚀 Fixed Defects	3
3	🚀 Accessibility Fixes	5
4	⭐ Improvements	5
5	🚀 Deployments	6
5.1	Infrastructure	6
5.2	CKAN	10
5.3	CRM	14
5.4	CDN	16
5.5	Bot	16
5.6	Web Apps	16
5.7	APIM	16
5.8	Platform APIs	16
5.9	B2C Tenant Policy Files	17
6	💻 Reviewers	18
7	Appendix	19
7.1	Running Pipeline from Tags	19








Release Note 
1	🔧What’s New

The following user stories are delivered as part of this SIT build: 
US Id 	Title	New ETA
21281	As a developer I want to use Azure purview API to scan the dataset and extract metadata	Completed
21235	As a Security Architect I'll perform handover sessions for HCF/HCM	Completed
8747	As a Consultant I will create custom reporting to monitor Cost Optimization	Completed
8915	As a Consultant I will create 5 pre-defined reports in a Dashboard to allow the Platform Owner to monitor aspects of consumption	Completed


List the deferred user stories and ETA: 
None.

 
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity
34046
FN-B2B Marketplace-Chrome/Safari/Edge - User is unable to create Organisation account.	2 - High
33064
FN-B2B-B2C-Welcome Email is single liner, not as per Template	3 - Medium
33239
FN - B2C My TASMU Portal - Safari - When user reset password by clicking forgot password link, success message is not displayed.	3 - Medium
33545
NF-Arabic - B2C My TASMU Portal - News titles in Homepage are in English	3 - Medium
33616
NF-Localization- Arabic- Session timeout popup is in English	3 - Medium
33688
NF-Localization-Arabic - B2B Market Place - Organization Registration Step 2- drop menu and banner are in English	3 - Medium
33738
NF-Logic Apps need to be edited after a new deployment to ensure functionality	3 - Medium
33745
NF-Localization-Arabic - B2C/B2B Market Place - unable to add payment method	3 - Medium
33753
FN-B2C- Profile name not getting updated on home page until user logout	3 - Medium
33917
NF-Localization-Arabic - My Account- Manage Subscriptions page localization issue	3 - Medium
33918
NF-Localization-Arabic - My Account- Order history page localization issue	3 - Medium
33919
NF-Localization-Arabic - My Account- Billing page localization issue	3 - Medium
33920
NF-Localization-Arabic - My Account- payments page localization issue	3 - Medium
33921
NF-Localization-Arabic - My Account- Pay now localization issue	3 - Medium
33951
FUNC-B2C/B2B - Contact Us - Error message is displayed when user click on Submit button. Also dev tool shows an error while uploading attachment.	3 - Medium
33989
NF-Localization-Arabic - My Account- Organization Profile	3 - Medium
34028
FN-CMS-News Article and Hero Web created remain in Draft state and does not appear for Translation	3 - Medium
34047
FN-B2B Marketplace-Safari/Chrome/Edge-Field is highlighted in red for pre-populated field	3 - Medium
34113
FN-Chatbot- "Other" option for providing Negative or Positive feedback is not available	3 - Medium
34132
NF-B2B/B2C - Global navigation does not adapt to ”Responsive Model”	3 - Medium
34139
FN-CMS-Hero Web intended for B2C Business owner, is displayed to other user .	3 - Medium
34143
Fun-B2B/B2C - Wrong Password validation	3 - Medium
34144
Fun-B2B/B2C - Password can contain the exclamation symbol (!)	3 - Medium
34149
NF-Storage accounts to use ZRS (Zone redundant storage)	3 - Medium
34157
FN-B2C My TASMU Portal/B2B Marketplace Portal - Safari/Chrome/Edge - Default country code (Qatar) is not set to any mobile number	3 - Medium
34159
FN- B2C- Error on Profile API when user is on home page	3 - Medium
34035
FN-B2B- Attached file is not shown in Support Request Details page	4 - Low
34161
FN- B2C- Products&Services menu shown instead of Smart Services for a B2C user while browsing the smart services catalog	4 - Low



Note:	The partial fix for bugs (Id# 33000 & 33748) is included in the current build. However, this is not a complete fix, and the respective bugs are NOT marked as “RESOLVED” by the development team yet. Therefore, this functionality should not be tested yet in this build. Kindly note, this is a new implementation that was discussed and agreed in the triage calls. The complete fix is targeted for the next SIT build on 25th March 2021.

Known issue: #34291 - Accounts pages: Menus are not aligned properly (MSFT backlog)




 
3	🚀 Accessibility Fixes
The following accessibility fixes are addressed as part of this release –
ID	Title
33122
NF-Accessibility-Create New Support Request-Label is missing for dropboxes
31489
NF-Accessibility-Homepage: Applies to all pages in the Arabic and English website-Images slider cause a confusion for screen reader
31491
NF-Accessibility-Homepage: Applies to all pages in the Arabic and English website-Make sure modal dialog is accessible
31508
NF-Accessibility-Contact us-Upload file
33061
NF-Accessibility-Select Plan – billing address forms page-Label is missing for dropboxes
33062
NF-Accessibility-Select Plan – billing address forms page-Error handling is disabled


4	⭐ Improvements

Timer Triggered function app for monitoring the content uploaded in CMS on a regular basis. 
 
5	🚀 Deployments
5.1	Infrastructure
Pull Request – https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/5448
Steps -
1.	Keep the copy of containers in below storage accounts in a temporary storage.
a.	st<sub>shrd<env>we01
b.	st<sub>appsstr<env>we01
c.	st<sub>appsint<env>we01
d.	st<sub>apimt<env>we01
2.	Delete the below resource from portal (environment will have downtime):
i.	evhns-<sub>-apps-mon-<env>-we-01
ii.	evhns-<sub>-shrd-<env>-we-01
iii.	st<sub>appsdiag<env>we01
iv.	st<sub>shrddiag<env>we01
v.	st<sub>shrd<env>we01
vi.	st<sub>appsstr<env>we01
vii.	st<sub>appsint<env>we01
viii.	st<sub>apimt<env>we01
ix.	redis-<sub>-apps-str-<env>-we-01
x.	cosmos-<sub>-apps-str-<env>-we-01
xi.	sb-<sub>-apps-strntf-<env>-we-01
xii.	sb-<sub>-apps-int-<env>-we-01
xiii.	logic-<sub>-apps-qnacopysync-<env>-we-01
xiv.	logic-<sub>-apps-qnakbsync-<env>-we-01
xv.	logic-<sub>-apps-intfile-<env>-we-01
xvi.	logic-<sub>-apps-6dhook-<env>-we-01
xvii.	logic-<sub>-apps-mpsd365-<env>-we-01
xviii.	logic-<sub>-apps-intprdt-<env>-we-01
xix.	logic-<sub>-apps-intsec-<env>-we-01
xx.	logic-<sub>-apps-mpso365-<env>-we-01
xxi.	logic-<sub>-apps-intsubs-<env>-we-01
xxii.	egd-<sub>-apps-int-<env>-we-01
xxiii.	agw-<sub>-apps-api-<env>-we-01
xxiv.	agw-<sub>-apps-api-<env>-we-01-ip
xxv.	agw-<sub>-apps-web-<env>-we-01
xxvi.	agw-<sub>-apps-web-<env>-we-01-ip
xxvii.	agw-<sub>-apps-ntf-<env>-we-01
xxviii.	agw-<sub>-apps-ntf-<env>-we-01-ip
xxix.	prvep-<sub>-apps-cosmos-<uat>-we-01
xxx.	prvep-<sub>-apps-cosmos-<uat>-we-01.nic.<guid>
3.	Add http to https redirection settings to application gateways (UAT can be taken as reference)
a.	agw-<sub>-apps-api-<env>-we-01
b.	agw-<sub>-apps-ntf-<env>-we-01
c.	agw-<sub>-apps-web-<env>-we-01
d.	Update the availability zones to 1,2,3 for above application gateways. (refer respective UAT files)
Port 80 must be enabled on the firewall for http to https redirection to work.
agw-cpd-apps-web-uat-we-01 has open data portal changes as well, they can be made separately as part of Section 5.2.
4.	Add parameter file for apicon-<sub>-apps-pflcds-<env>-we-01. 
a.	Client Id parameter is the Client Id of App Registration - spn-crm-profile-management-integration-<env> from Azure AD.
5.	Add parameter file for logic-cpd-apps-intacnt-<env>-we-01.
6.	Add the new api connection and logic app in integration resource group (rg-<sub>-apps-int-<env>-we-01)
7.	Update the below logic apps for new changes (take uat changes as reference)
a.	logic- <sub> -apps-intaprv1-<env>-we-01
b.	logic- <sub> -apps- intgbaprl -<env>-we-01
c.	logic- <sub> -apps- inttrsl -<env>-we-01
8.	Update the below storage accounts to Standard_ZRS
a.	st<sub>appsdiag<env>we01
b.	st<sub>shrddiag<env>we01
c.	st<sub>shrd<env>we01
d.	st<sub>appsstr<env>we01
e.	st<sub>int<env>we01
f.	st<sub>apimt<env>we01
9.	Update the below event hub namepace to include zoneRedundant parameter with value as true.
a.	evhns-<sub>-apps-mon-<env>-we-01
b.	evhns-<sub>-shrd-<env>-we-01
10.	Update the cosmos-<sub>-apps-str-<env>-we-01 to include zoneRedundancy in location (refer UAT file)
11.	Update the redis-<sub>-apps-str-<env>-we-01 to include 3 availability zones (refer UAT file and module version - 2020-06-01)
12.	Add the CI pipeline to ADO for new Redis module.
13.	 Update the below service bus to include zoneRedundant parameter with value as true.
a.	sb-<sub>-apps-strntf-<env>-we-01
b.	sb-<sub>-apps-int-<env>-we-01
14.	Update below key vault access policies for object Id of ADO Service Principal:
a.	kv-<sub>-pltf-<env>-we-01
b.	kv-<sub>-apps-<env>-we-01
c.	kv-<sub>-apps-pt-<env>-we-01
 
15.	Update the apim-<sub>-shrd-<env>-we-01 to include parameters requestThreshold (value – “1000”), durationThreshold (“10000”) and actionGroupId (value will be specific to env) refer UAT file.
16.	Move the below logic apps to rg-<sub>-apps-int-<env>-we-01
a.	logic-<sub>-apps-qnacopysync-<env>-we-01
b.	logic-<sub>-apps-qnakbsync-<env>-we-01
17.	Update the resource dependencies in deployment orchestration of rg-<sub>-apps-int-<env>-we-01 (take reference from UAT)
18.	Deploy below resource groups:
a.	rg-<env->-shrd-mon-<env>-we-01
b.	rg-<env->-apps-mon-<env>-we-01
c.	rg-<cpd>-pltf-sec-<env>-we-01
d.	rg-<cpd>-apps-sec-<env>-we-01
e.	rg-<env->-shrd-<env>-we-01
f.	rg-<env->-apps-str-<env>-we-01
g.	rg-<env>-apps-net-<env>-we-01
h.	rg-<env->-apps-cog-<env>-we-01
i.	rg-<env->-apps-int-<env>-we-01
j.	rg-<env->-apps-pt-<env>-we-01
k.	rg-<env->-apps-waf-<env>-we-01
19.	Restore the containers for below storage accounts (backup taken in step 1):
a.	st<sub>shrd<env>we01
b.	st<sub>appsstr<env>we01
c.	st<sub>appsint<env>we01
d.	st<sub>apimt<env>we01
20.	ITSM has a logic app subscribing to egd-<sub>-apps-int-<env>-we-01. It needs to re-deployed, or the subscription needs to be added to the event grid domain. Get in touch with ITSM POC.

21.	Update below variable groups and key vault secrets:
a.	CDNSettings-StorageAccount
b.	ConnectionStrings-IntegrationServiceBus
c.	Cms-Function-ServiceBusConnectionString
d.	ConnectionStrings-Redis
e.	ConnectionStrings-StorageAccount
f.	ConnectionStrings-CosmosDBAuthKey
g.	EventGridSettings-DomainKey
h.	NotificationSettings-NotificationServiceBusConnectionString
 

5.2	CKAN
5.2.1	Pre-requisites for CKAN deployments:
1.	IP planning for the CKAN Subnets – 3 subnets will be required for CKAN, a default subnet for all the VMs, a subnet for Redis cache and a subnet for application gateway.
2.	UDR needs to be applied to the subnets to take the traffic to the Azure Firewall. Similar UDR that has been used for UAT will be created for PRE.
3.	There exists a rule in the Azure Firewall – allow-ckan-internet-outbound that allows the CKAN traffic outbound. Add the PRE subnet address space after deploying the subnets needed for CKAN.
4.	One time acceptance of Bitnami license agreement from the subscription 
i.	Create the temporary solution from azure portal for CKAN with Azure Database for PostgreSQL Hyperscale in a resource group – rg-<sub>-apps-ckan-temp-we-01.
ii.	Pass any sample parameter values.

 

iii.	Resource group can be deleted immediately. This is one time activity only to accept the license agreement to enable automated deployments.
5.	Seed the below secrets in below key vaults to be used by ARM templates. 
Secret Name	Key Vault 	Parameter File	Usage
Ckan-AppPassword	kv-<sub>-apps-<env>-we-01	ckan-<sub>-apps-<env>-we-01	appPassword
Ckan-AdminUsername	kv-<sub>-apps-<env>-we-01	ckan-<sub>-apps-<env>-we-01	adminUsername
Ckan-AdminPassword	kv-<sub>-apps-<env>-we-01	ckan-<sub>-apps-<env>-we-01	adminPassword
Ckan-DatabasePassword	kv-<sub>-apps-<env>-we-01	ckan-<sub>-apps-<env>-we-01	databasePassword
<env>-SQCP-Certificate	kv-<sub>-pltf-<env>-we-01	ckan-<sub>-apps-<env>-we-01	sslCertificates
5.2.2	Deployment Steps CKAN:
1.	Add resource group parameter file rg-<sub>-apps-ckan-<env>-we-01 in Resource Groups module.
2.	Add route table parameter file route-<sub>-apps-ckndflt-<env>-we-01-parameters.json (Refer UAT file).
3.	Add route table to deployment orchestration in rg-<sub>-apps-net-<env>-we-01 and deploy.
4.	Add network security groups parameter files, 
i.	nsg-<sub>-apps-ckndflt-<env>-we-01
ii.	 nsg-<sub>-apps-cknagw-<env>-we-01,
iii.	nsg-<sub>-apps-cknredis-<env>-we-01
5.	Add network security groups to deployment orchestration in rg-<sub>-apps-sec-<env>-we-01 and deploy.
6.	Add 3 subnets
i.	snet-<sub>-apps-ckndflt-<env>-we-01
ii.	snet-<sub>-apps-cknagw-<env>-we-01
iii.	 snet-<sub>-apps-cknredis-<env>-we-01
 in vnet-<sub>-pltf-<env>-we-01
7.	Deploy rg-<sub>-pltf-net-<env>-we-01 to deploy subnets to the vnet.
8.	Add parameter file for
 

9.	For logic-<sub>-apps-purvckan-<env>-we-01, the following are environment specific parameters, so update accordingly - 

Variable	Value	Example (UAT)
ckanbaseurlwithversion	https://opendata.<env>.sqcp.qa/api/3/action	https://opendata.uat.sqcp.qa/api/3/action
blobfilesbasepath	https://dlsopenzone<env>we01.blob.core.windows.net	https://dlsopenzonedevwe01.blob.core.windows.net
Purview_acquire_access_token_http	https://login.microsoftonline.com/<tenantID>/oauth2/token	https://login.microsoftonline.com/92603419-35d1-4eb0-8427-cac731071355/oauth2/token
Purview_append_encoded_blob_static_path
	https://dlsopenzone<env>we01.dfs.core.windows.net	https://dlsopenzonedevwe01.dfs.core.windows.net
Purview_declare_unique_attribute_url_variable
	https://purv-cpd-data-<env>-we-01.catalog.purview.azure.com/api/atlas/v2/entity/uniqueAttribute/type/azure_datalake_gen2_path	https://purv-cpd-data-dev-we-01.catalog.purview.azure.com/api/atlas/v2/entity/uniqueAttribute/type/azure_datalake_gen2_path
10.	Add new resource group deployment folder in deployment orchestration for rg-<sub>-apps-ckan-<env>-we-01 and add 
i.	ckan-<sub>-apps-<env>-we-01, 
ii.	intac-<sub>-apps-int-<env>-we-01, 
iii.	logic-<sub>-apps-purvckan-<env>-we-01
iv.	apicon-<sub>-apps-dlszn-<env>-we-01
v.	apicon-<sub>-apps-ckankv-<env>-we-01
11.	Add secrets Ckan-Authorization-Token and Purview-AcquireAccess-TokenReqBody in Scripts/KeyVault/all-secrets-<env>.yml (Refer all-secrets-npd.yml).
12.	Update the above two secrets in variable groups and key vault (kv-<sub>-apps-<env>-we-01)
13.	Deploy Key Vault and App Configuration pipelines. (deploy the ckan app configuration only after the secrets have been seeded, it will break all the solutions if config store is not able to find the secrets)
14.	In agw-<sub>-apps-web-<env>-we-01
i.	Add open data portal httpsettings, listener, rule, probe and backend pool
ii.	Backend pool IP of agw-<sub>-apps-ckan-<env>-we-01
iii.	Add below parameter for exclusion rule
"firewallExclusions": {
            "value": [
                {
                    "matchVariable": "RequestCookieNames",
                    "selectorMatchOperator": "StartsWith",
                    "selector": "auth_tkt"
                }
            ]
        	}
15.	Create and run the pipelines for new modules in ADO.
i.	BitnamiCkan
ii.	IntegrationAccount
16.	Deploy rg-<sub>-apps-ckan-<env>-we-01.
17.	Deploy rg-<sub>-apps-waf-<env>-we-01.
18.	More details regarding configuration of CKAN are in shared technical design document.
 
5.3	CRM
Manual core solution import mentioned below is needed before the CD-CRM pipeline is approved for the respective environment.
 
 


Build Id	Pipeline Name
34182	CD-CrmPlatform-Release


After deployment, it needs to be verified if workflows are activated or not. If not activated, then follow the below steps:
In Test Environment below were in Draft state:
Case: Status Change Notification
External Note: Notify External Note Created
Steps to Activate:
Go to Process -> Check if any Process is in Draft state -> If any of the Process is in Draft state then open that Process -> Solution Layer->Remove Active Customizations->Ok.
 
Again, close the workflow. Again, re open the workflow and click on "Activate" button.
 

5.4	CDN
Tag	Pipeline Name
SIT_CDN_18Mar2021	CD-CDNContainer-Prd-Release


5.5	Bot
Tag	Pipeline Name
SIT_Bot_18Mar2021	CD-BotApi-Prd-Release


Note: Due to an issue in West Europe region luis tra function app deployment fails sometimes.
https://github.com/projectkudu/kudu/issues/3042
Work Around:
1.	Change the app service plan of plan-<sub>-apps-cog-<env>-we-01 to P2V2
2.	Re-run the stage.
3.	Revert the app service plan of plan-<sub>-apps-cog-<env>-we-01 to P1V2

5.6	Web Apps
Tag	Pipeline Name
SIT_Web_18Mar2021	CD-WebApps-Prd-Release


5.7	  APIM 
Tag	APIs	Pipeline Name
SIT_APIM_18Mar2021	MarketplaceCatalogueApi;
	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_18Mar2021	MarketplaceCatalogueApi;	CD-APIMConfig-pre-Release


5.8	Platform APIs
Tag	Pipeline Name
SIT_API_18Mar2021	CD-PlatformAPIs-Prd-Release


1.	After successful run of the pipeline, retrieve and update below variable groups and key vault secrets:
a.	PaymentGWSettings-GetPaymentPreferenceServiceURL
b.	PaymentGWSettings-UpdatePaymentPreferenceServiceURL
c.	Cms-Function-NotificationUrl
2.	 Run CD-AppConfiguration-Master-Release to refresh the config and for applications to fetch new configuration and secrets.

5.9	B2C Tenant Policy Files
1.	Upload new policy files. Tag - SIT_Web_18Mar2021
2.	File names below:
a.	B2C_1A_B2B_TrustFrameworkBase_<env>.xml
b.	B2C_1A_B2B_TrustFrameworkExtensions_<env>.xml
c.	B2C_1A_BO_TrustFrameworkBase_<env>.xml
d.	B2C_1A_BO_TrustFrameworkExtensions_<env>.xml
e.	B2C_1A_TrustFrameworkBase_<env>.xml
f.	B2C_1A_TrustFrameworkExtensions_<env>.xml
g.	B2C_1A_TrustFrameworkExtensions_linking_<env>.xml
3.	Please apply any B2C policy customizations selectively done for pre prod environment. 
 
6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca, Vijay Kolli
Approved by 	Ashwani Sharma

 
7	Appendix
7.1	 Running Pipeline from Tags
 

