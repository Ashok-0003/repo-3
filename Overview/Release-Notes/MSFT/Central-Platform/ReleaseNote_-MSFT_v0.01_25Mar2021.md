[ReleaseNotes_ MSFT_v0.01_25Mar2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_25Mar2021-efa6d040-e539-4668-9460-51352a947c73.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
2.1	Known Issues:	4
3	⭐ Improvements	5
3.1	CMS	5
3.2	CRM	5
4	🚀 Deployments	5
4.1	Infrastructure	5
4.2	CRM	7
4.3	CDN	7
4.4	Platform APIs	7
4.5	Web Apps	7
4.6	APIM	7
4.7	Mobile	8
4.8	B2C Tenant Policy Files	8
4.9	Data Resources	8
5	💻 Reviewers	8
6	Appendix	9
6.1	Running Pipeline from Tags	9








Release Note 
1	🔧What’s New

New user stories delivered: None
ID	Title	State
19269
As platform operator i need to update all TASMU logos used in Report/Dashboard to reflect the latest update of the logo shared by TASMU	Test Complete

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity
33000
FN - B2B Marketplace - Sf - When clicked on profile icon only Logout option is displayed.	2 - High
33158
FN-B2C- User is not able to see profile details when logged in with Facebook credentials	3 - Medium
34007
FUNC-B2B-B2C- Only Authorized user can subscribe to product as per target customer segment Failed	2 - High
34142
NF-My TASMU App - iOS - The hero boxes are not rendering properly	3 - Medium
34158
FN-My TASMU App Android- Confirm & Pay button is enabled even though Terms & Conditions and End User License Agreement checkboxes are unchecked	4 - Low
34165
FN - iOS - "Products and Services" is not visible in Category drop-down for Create Support request	3 - Medium
34167
FN-B2B Marketplace-Safari/Chrome - When user deletes an attached file, file dialogue opens	3 - Medium
34169
NF-My TASMU App - iOS - Arabic- Back key label	3 - Medium
34217
FN - My TASMU App - Android/ios- Error shown on clicking phone number in Contact Us page	3 - Medium
34228
FN - My TASMU App - Android- User is able to enter Passport number without selecting Passport Country	3 - Medium
34230
FN-SmartCity- User is not able to navigate between different sectors	3 - Medium
34244
FN-Portal-Once user is logged out from profile page, user is still logged in on Home page.	3 - Medium
34247
FN-B2B- Registration for Organization is not asked when Anonymous user raise a request from Chatbot	2 - High
34267
FN-Portal-Expiry date of a subscription is not correct	3 - Medium
34295
FN-B2B/B2C- Chatbot: Leave a message: User can't edit the message and email	3 - Medium
34296
FN-B2C/B2B - User Profile: Address: Field length is 80 characters for City and 20 for PO Box	3 - Medium
34397
FN-My TASMU App - iOS - Mobile app crashes after changing password from My Account section	2 - High
34399
FN - My TASMU App Android- UI issue for linked accounts in Accounts page	3 - Medium
34413
NF-My TASMU App - iOS - Arabic- Arabic Text is flipped in different places	3 - Medium
34448
FN-My TASMU App- iOS - Mobile App crashes when login through LinkedIN	1 - Critical
34541
FN-Portal-After user logs out, another user is able to access My account page of the user	1 - Critical

2.1	Known Issues:
a)	The localized content is being waited upon for approvals. As part of bug fix 34007, the below pop-ups were introduced. 

b)	As part the bug fixes (33000, 33158) the below pop-ups are introduced. Waiting for the approved localized contents of the pop-up and KB articles.  The content of the KB article is not approved however, the content of the pop-up is approved.                   
c)	As part of the 34007, subscription of the products and services with the existing credentials, is not possible, as the profiles lack the customer segmentation. Hence accordingly the data should be configured in CRM system.


3	⭐ Improvements
3.1	CMS
1.	 Waiting time of the trigger is decreased from 3 minutes to 1 minute so that approval process can be speeded up.
2.	Sync Sector function app will be triggered for every 24 hours, which was 5 minutes earlier, so that load is reduced.
3.	“Copy CDN URL” functionality has been introduced in all document/image library so that CDN URL for contents can be copied with ease, which will increase the Usability. 
3.2	CRM
1.	Session affinity related setting change to compliment scale improvements being done at Dynamics (product) environment through support team.
Further performance testing should be done only after this release, as well as additional environment preparation. For CRM, the environment type must be of ‘production’ (not ‘sandbox’), and dynamics web servers must be scaled out to minimum six servers to overcome API throttling (this can be done through product support request or ICM ticket). Both Platform APIs and CRM builds need to go for this performance improvement.
 
4	🚀 Deployments
4.1	Infrastructure
Pull Request –  https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/5668
Steps:
1.	Keep the backup of consumption container from below storage account:
a.	st<sub>globacmwe01
2.	Delete the below storage account:
a.	st <sub>globacmwe01
3.	Delete the following resources (if present) from azure portal - 
a.	func-<sub>-apps-o365-<env>-we-01
b.	func-<sub>-apps-d365-<env>-we-01
4.	Remove the following ARM template parameter files from Modules/ARM/FunctionApps - 
a.	func-<sub>-apps-o365-<env>-we-01-parameters.json
b.	func-<sub>-apps-d365-<env>-we-01-parameters.json
5.	Remove the deployment orchestration code for the function apps mentioned in Step 2 from DeploymentOrchestration/Environments/<sub>/<env>/rg-<sub>-apps-int-<env>-we-01/deploy.json
6.	Update the sku for StorageAccount - st<sub>globacmwe01 to Standard_ZRS
7.	Update the following logic apps for new changes (UAT reference)
a.	logic-<sub>-apps-intaprv1-<env>-we-01-parameters.json
b.	logic- <sub> -apps-intgbaprl-<env> -we-01-parameters.json
c.	logic- <sub> -apps-inttrsl -<env> -we-01-parameters.json
8.	Private end point implementation for sb-<sub>-apps-strntf-<env>-we-01
a.	Update vnet-<sub>-pltf-<env>-we-01 ARM template for adding service endpoints to subnets - snet-<sub>-apps-aks-<env>-we-01 and snet-<sub>-apps-bkend-<env>-we-01
,
{
  "service": "Microsoft.ServiceBus",
  "locations": [
    "westeurope"
  ]
}

b.	Add template for private dns zone - <sub>-privatelink.servicebus.windows.net
c.	Add it to deployment orchestration of rg-<sub>-pltf-net-<env>-we-01 (For CPD, the <env> here is dev as private dns zones is only created once in a subscription)
d.	Add parameter for private endpoint like prvep-<sub>-apps-sbstrntf-<env>-we-01
i.	PrivateDnsZoneId  is resource Id of <sub>-privatelink.servicebus.windows.net
ii.	Within two different environments, this resource Id of private dns zone will remain same.
e.	Add the private end point to deployment orchestration of rg-<sub>-apps-net-<env>-we-01
f.	Move and update the below parameter files of ServiceBusNamespace
i.	sb-<sub>-apps-strntf-<env>-we-01 (module version - 2021-03-18)
ii.	Make the module version update in deployment orchestration as well.
g.	Add the CI pipeline for new module – CI-ServiceBusNamespace-20210318-Master-Build
h.	Rename the existing to CI-ServiceBusNamespace-20170401-Master-Build
9.	Key Vault purge protection enabled for following key vaults:
a.	Create CI pipeline for new module - 
i.	CI-KeyVault-20210323-Master-Build
ii.	Rename existing to CI-KeyVault-20191128-Master-Build	
b.	Move and update the below parameter files to 2021-03-23 and update deployment orchestration files as well. (refer UAT)
Key Vault	Soft Delete	Soft Delete Retention Days	Purge Protection	Remarks
kv-<sub>-apps-<env>-we-01	true	7	true	 
kv-<sub>-apps-pt-<env>-we-01	true	7	true	 
kv-<sub>-pltf-<env>-we-01	true	90	true	Retention days were already set to 90 and can’t be changed now.

10.	Deploy the following resource groups:
a.	rg-<sub>-glob-acm-we-01
b.	Upload the containers content to st<sub>globacmwe01 (backup taken in step 1)
c.	Update the secret ConnectionStrings-ConsumptionStorageAccount in Key Vault (kv-<sub>-apps-<env>-we-01) with connection string of st<sub>globacmwe01
d.	rg-<sub>-pltf-net-<env>-we-01 (For CPD, the <env> here is dev as private dns zones are one per subscription)
e.	rg-<sub>-apps-net-<env>-we-01
f.	rg-<sub>-pltf-sec-<env>-we-01
g.	rg-<sub>-apps-sec-<env>-we-01
h.	rg-<sub>-apps-pt-<env>-we-01
i.	rg-<sub>-apps-str-<env>-we-01
j.	rg-<sub>-apps-int-<env>-we-01
11.	kv-cpp-apps-pre-we-01 has an issue in pre prod environment with sqcp-ado-spn being greyed out in access policies. Check if it needs manual intervention after deployment. (work with support team on permanent resolution of this)
 
4.2	CRM
Build Id	Pipeline Name
35772	CD-CrmPlatform-Release 


4.2.1 Verify workflows are activated of deployment guide
Manual Steps for CRM:
Two KB articles (One for english and other for Arabic) need to be created in the CRM environment and update the trackingId and trackingId_AR with respective article Ids in environment specific variable section of CD-WebApps-Release and CD-WebApps-Prd-Release (This is already done for pre)

4.3	CDN
Tag	Pipeline Name
SIT_CDN_25Mar2021	CD-CDNContainer-Prd-Release


4.4	Platform APIs
Tag	Pipeline Name
SIT_API_25Mar2021	CD-PlatformAPIs-Prd-Release


4.5	Web Apps
Tag	Pipeline Name
SIT_Web_25Mar2021	CD-WebApps-Prd-Release


4.6	  APIM 
Tag	APIs	Pipeline Name
SIT_APIM_25Mar2021	MarketplaceCatalogueApi;
	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_25Mar2021	MarketplaceCatalogueApi;	CD-APIMConfig-pre-Release


4.7	Mobile
Platform	Build Id	Pipeline Link
Android	35941	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=35941&view=results

iOS	35942	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=35942&view=results


4.8	B2C Tenant Policy Files
1.	Upload the policy files. Source – Tag - SIT_Web_25Mar2021
a.	B2C_1A_B2B_TrustFrameworkBase_<env>.xml
b.	B2C_1A_B2B_TrustFrameworkExtensions_<env>.xml
c.	B2C_1A_BO_TrustFrameworkBase_<env>.xml
d.	B2C_1A_BO_TrustFrameworkExtensions_<env>.xml
e.	B2C_1A_TrustFrameworkBase_<env>.xml
f.	B2C_1A_TrustFrameworkExtensions_<env>.xml
g.	B2C_1A_TrustFrameworkBase_linking_<env>.xml
h.	B2C_1A_TrustFrameworkExtensions_linking_<env>.xml
2.	Please apply any B2C policy customizations selectively done for pre prod environment. Eg: Disabling email verification check on registration.

4.9	Data Resources
PowerBI reports have been amended and are to be used as samples by Malomatia to update the PowerBi reports in pre-production. 
It is a manual deployment, requires download of pbix files, amending the data sources to consume it from pre-prod service, upload the pbix files into PowerBI service.
 

5	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma


6	Appendix
6.1	 Running Pipeline from Tags
 
