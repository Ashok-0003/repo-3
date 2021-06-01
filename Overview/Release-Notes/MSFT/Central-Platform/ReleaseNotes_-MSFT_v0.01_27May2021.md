[ReleaseNotes_ MSFT_v0.01_27May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_27May2021-3d41cc91-6899-40ee-bb55-28ac2ef87748.docx)

Contents
1	🔧What’s New	2
2	⭐ Improvements	2
3	🚀 Deployments	3
3.1	Infrastructure	3
3.2	CRM	4
3.2.1	Deployment	4
3.2.2	CRM Post Deployment Verification	4
3.2.3	CRM Email Template Links Update	4
3.3	Platform APIs	4
3.4	Web Apps	4
3.5	APIM	5
4	💻 Reviewers	6
5	Appendix	7
5.1	Post Deployment Verification	7
5.2	Running Pipeline from Tags	7

 
Release Notes
1	🔧What’s New
New user stories delivered: None
2	⭐ Improvements
Infra:
1.	https for agw-<sub>-apps-web-<env>-we-01 backend
2.	https for apim-<sub>-shrd-<env>-we-01 APIs hosted on AKS
CRM:
Added Not Applicable Districts.
 
3	🚀 Deployments
3.1	Infrastructure
Pull Request – https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/7079
Steps:
1.	Add/Update following parameter files (refer UAT files) -
Module	Parameter Files	Action	Properties
LogicApp	logic-<sub>-apps-route-<env>-we-01	Update	Refer UAT

ApiConnectionLogAnalytics	apicon-<sub>-apps-log-<env>-we-01	Add
	Refer UAT
ApplicationGateway	agw-<sub>-apps-web-<env>-we-01	Update
	Refer UAT
(done for pre/prd)
ApplicationGateway	agw-<sub>-apps-aks-<env>-we-01	Update
	sslCertificates,
managedIdentityId
(done for pre/prd)
ManagedIdentity	mi-<sub>-apps-agwaks-<env>-we-01	Add	Refer UAT
(done for pre/prd)
KeyVault	kv-<sub>-pltf -<env>-we-01	Update	Access policy for get certificate to ObjectId of mi-<sub>-apps-agwaks-<env>-we-01
(done for pre/prd)

Add the new resources to respective deployment orchestrations.
2.	apicon-<sub>-apps-log-<env>-we-01  to rg-<sub>-apps-int-<env>-we-01
3.	mi-<sub>-apps-agwaks-<env>-we-01 to rg-<sub>-apps-aks-<env>-we-01 (done for pre/prd)
4.	Role Assignments required  (done for pre/prd)
Identity Name	Type	Target Resource	Role
mi-<sub>-apps-aks-<env>-we-01	Managed Identity	mi-<sub>-apps-agwaks-<env>-we-01	Managed Identity Operator

5.	From the jump VM uninstall ingress release from both pre and prd to apply update on agw aks using below command (done for pre/prd)
helm uninstall ingress-azure -n ingress

6.	Deploy the following pipelines –
a.	CD-rg-<sub>-pltf-sec-<env>-we-01-Master-Release  (done for pre/prd)
b.	CD-rg-<sub>-apps-aks-<env>-we-01-Master-Release  (done for pre/prd)
c.	CD-rg-<sub>-apps-waf-<env>-we-01-Master-Release (done for pre/prd)
d.	CD-rg-<sub>-apps-int-<env>-we-01-Master-Release

3.2	CRM
3.2.1	Deployment
Build Id	Pipeline Name
43905	CD-CrmPlatform-Release


3.2.2	CRM Post Deployment Verification
  Verify workflows and business rules are activated from deployment guide (Refer 5.16 section) 

3.2.3	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)

3.3	Platform APIs
(done for pre/prd)
Tag	Pipeline Name
SIT_API_27May2021	CD-AKS-Release (stages – build, pre, prd)

SIT_API_27May2021	CD-PlatformAPIs-Prd-Release


3.4	Web Apps
(done for pre/prd)
Tag	Pipeline Name
SIT_Web_27May2021	CD-WebApps-Prd-Release

 
3.5	  APIM 
(done for pre/prd)
Pipeline – CI-APIMConfig-CentralPlatformCore-Master-Prd-Build
Variables – cmscontentapi;cmsdocumentsapi;cmsmediaassetsapi;KnowledgeBaseAPI;Case;FieldService;OrganisationProfile;Profile;MarketplaceCatalogue;Demographic;Config;NotificationApi;SMSProviderApi;SMSPublisherApi;NotificationTemplate;PaymentApi;

Tag - SIT_APIM_27May2021
Pipeline – CI-APIMConfig-Productization-Master-Prd-Build

Variables – NotificationGSmsApi;NotificationSmsFreeApi;NotificationSmsStandardApi;NotificationSmsPremiumApi;NotificationEmailFreeApi;NotificationEmailStandardApi;NotificationEmailPremiumApi;PushNotificationFreeApi;PushNotificationStandardApi;PushNotificationPremiumApi;SubscriptionStandardApi;SubscriptionPremiumApi;

Tag - SIT_APIM_27May2021
Pipeline – CI-APIMConfig-SMSGatewayservice-Master-Prd-build

Variables – SMSGatewayDomesticApi;SMSGatewayInternationalApi

Tag - SIT_APIM_27May2021
Pipeline – CD-APIMConfig-pre-Release

Variables – cmscontentapi;cmsdocumentsapi;cmsmediaassetsapi;KnowledgeBaseAPI;Case;FieldService;OrganisationProfile;Profile;MarketplaceCatalogue;Demographic;Config;NotificationApi;SMSProviderApi;SMSPublisherApi;NotificationTemplate;PaymentApi;NotificationGSmsApi;NotificationSmsFreeApi;NotificationSmsStandardApi;NotificationSmsPremiumApi;NotificationEmailFreeApi;NotificationEmailStandardApi;NotificationEmailPremiumApi;PushNotificationFreeApi;PushNotificationStandardApi;PushNotificationPremiumApi;SubscriptionStandardApi;SubscriptionPremiumApi;SMSGatewayDomesticApi;SMSGatewayInternationalApi

Tag - SIT_APIM_27May2021
Pipeline – CD-APIMConfig-prd-Release

Variables – cmscontentapi;cmsdocumentsapi;cmsmediaassetsapi;KnowledgeBaseAPI;Case;FieldService;OrganisationProfile;Profile;MarketplaceCatalogue;Demographic;Config;NotificationApi;SMSProviderApi;SMSPublisherApi;NotificationTemplate;PaymentApi;NotificationGSmsApi;NotificationSmsFreeApi;NotificationSmsStandardApi;NotificationSmsPremiumApi;NotificationEmailFreeApi;NotificationEmailStandardApi;NotificationEmailPremiumApi;PushNotificationFreeApi;PushNotificationStandardApi;PushNotificationPremiumApi;SubscriptionStandardApi;SubscriptionPremiumApi;SMSGatewayDomesticApi;SMSGatewayInternationalApi

Tag - SIT_APIM_27May2021
4	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
5	Appendix
5.1	Post Deployment Verification
1.	Function Apps Running 
a.	https://func-cpp-apps-ckan-pre-we-01.azurewebsites.net/ 
b.	https://func-cpp-apps-qnasync-pre-we-01.azurewebsites.net/ 
c.	https://func-cpp-apps-luistra-pre-we-01.azurewebsites.net/ 
d.	https://func-cpp-apps-intbpa-pre-we-01.azurewebsites.net/ 
e.	https://func-cpp-apps-intntf-pre-we-01.azurewebsites.net/ 
f.	https://func-cpp-apps-pt-pre-we-01.azurewebsites.net/ 
2.	Marketplace Portal - https://marketplace.pre.sqcp.qa/en/ 
3.	Bot – Chat with bot on marketplace 
4.	My Tasmu Portal - https://mytasmu.pre.sqcp.qa/en/ 
5.	Account Portal - https://account.pre.sqcp.qa/en/ 
6.	Admin Portal Portal - https://cpadmin.pre.sqcp.qa  (Login screen should come) 
7.	API Config access - https://api.pre.sqcp.qa/config/api/feature 
8.	Open Data Portal - https://opendata.pre.sqcp.qa/

5.2	Running Pipeline from Tags
 
