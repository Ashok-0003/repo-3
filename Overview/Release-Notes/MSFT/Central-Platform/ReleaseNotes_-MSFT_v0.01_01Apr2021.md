[ReleaseNotes_ MSFT_v0.01_01Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_01Apr2021-30abbd00-4bcb-4ed5-b737-4f55deecd0ec.docx)

Release Note 
1	🔧What’s New

New user stories delivered: None

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
34541
FN-Portal-After user logs out, another user is able to access My account page of the user	1 - Critical	1
32962
FN-B2C- User is unable to link Facebook account on the Linked Accounts page	3 - Medium	1
33041
NF-Localization-Arabic - B2B Market Place - Text not translated in Configure plan page	3 - Medium	2
33164
FN - B2B Marketplace - UI issue observed on homepage (inconsistent)	3 - Medium	1
33207
FN - Email format for Case Auto Response is not correct	3 - Medium	1
34134
NF-B2C-The contents within boxes do not render properly and completely.	3 - Medium	1
34140
FN-B2C- Pop-up is displayed whenever user logs out from Account URL	3 - Medium	1
34157
FN-B2C My TASMU Portal/B2B Marketplace Portal - Safari/Chrome/Edge - Default country code (Qatar) is not set to any mobile number	3 - Medium	2
34238
FN-Portal-User is able to set preferred mode of contact as SMS, even when there is no mobile number added to profile	3 - Medium	1
34452
FN-When account of the user is suspened, its status is dispalyed as '2'	3 - Medium	1
34459
FN-B2B- Error Code: 400 shown on searching with special characters in Search box	3 - Medium	2
34508
UI-B2B Marketplace Portal - Login and Register buttons are not displayed when user tries to subscribe to a service as anonymous user	3 - Medium	1
34581
FN - B2C/B2B - Currency is not shown in order screen	3 - Medium	1
34626
FN-B2C- User is not getting redirected to "Create Support Request" and "Create Service Request" page when clicked on "Create Support Request" and "Create Service Request" buttons respectively	3 - Medium	2
34635
FN-B2C- Products & Services/Smart Services link is not working	3 - Medium	1
34652
FN - B2B/B2C- Error shown on homepage	3 - Medium	1
34300
FN-B2B/B2C- Knowledge Base: Article Description is less than 100 characters	4 - Low	4

Note:
	For Bug 33987, MSFT has included localization for currency.
	For Bug 33207, MSFT has changed the template for English and Arabic (Arabic is Google translated for now). Once the email content is finalized, the same can be updated in the CRM back-end system.
	For the bug # 34486, MSFT team has made partial code changes as this bug was assigned to MSFT today (1-Apr-2021). Due to this partial code change, the download invoice API is not working as expected as is under development. This will be available on Monday.
3	🚀 Accessibility fixes

The following issues related to accessibility have been addressed in this build -
ID	Title
34376
34376
NF-Logged In user Homepage B2BProducts & Services items must have role as tab, stats as collapse & expanded.
31489
31489
NF-Accessibility-Homepage: Applies to all pages in the Arabic and English website-Images slider cause a confusion for screen reader
31493
31493
NF-Accessibility-Homepage: Applies to all pages in the Arabic and English website-Keyboard users can’t access to the pause button to pause the slider
33042
33042
NF-Accessibility-Registration: (Applies to B2B & B2C)-Error handling
33049
33049
NF-Accessibility-Products & Services on homepage-On Focus for Mouse and Keyboard users
33053
33053
NF-Accessibility-Products & Services the entire page-Incorrect tab order is discovered
34363
34363
NF-Accessibility-Contact us-Page enhancement
34379
34379
NF-B2C-Smart Services – inner page issues
34381
34381
NF-B2C-Smart Services – Enhancements
34517
34517
NF-Accessibility-logged in user: (Applies to B2B & B2C)-collapse icons


4	⭐ Improvements
4.1	 CMS 
1.	SharePoint Webhook trigger for any change in list and library, should be routed via APIM to intntf function app.
 
5	🚀 Deployments
5.1	Infrastructure
Pull Request –  https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/5844
Steps: 
1.	Update and move parameter files of following application gateways (Module - 2020-03-26)
a.	agw-<sub>-apps-api-<env>-we-01
b.	agw-<sub>-apps-ntf-<env>-we-01
c.	agw-<sub>-apps-web-<env>-we-01
2.	Add parameters - sslPolicyType, sslPolicyName, wafPolicyName, managedRuleSets, firewallEnabled, customRules (refer corresponding UAT file)
3.	Change the module version in Deployment Orchestration for the above 3 application gateways as well.
4.	Update logic-<sub>-apps-purvckan-<env>-we-01 for below change at two places (Refer UAT)
a.	"x-ckan-request": "true"
5.	Add parameter files of following ARM templates:
a.	ApiManagementCMSNotificationAPI - apimcms-<sub>-shrd-<env>-we-01-parameters.json (Refer UAT)
b.	ApiManagementFunctionAppBackend – apimfab-<sub>-shrd-<env>-we-01-parameters.json (Refer UAT)	

6.	Update Deployment Orchestartion file for pre and prod environments – rg-<sub>-shrd-<env>-we-01 delpoy.json files and add the entries for the following  :
a.	DEP-apimfab-<sub>-shrd-<env>-we-01 (Refer UAT)
b.	DEP-apimcms-<sub>-shrd-<env>-we-01 (Refer UAT)

7.	 Add the following CI pipelines:
a.	CI-ApiManagementCMSNotificationAPI-Master-Build
b.	CI-ApiManagementFunctionAppBackend-Master-Build

8.	Deploy the below resource groups:
a.	rg-<sub>-apps-waf-<env>-we-01
b.	rg-<sub>-shrd-<env>-we-01

9.	Deploy CD-AppConfigurations-Master-Release

 
 
5.2	CRM
5.2.1	CRM manual pre deployment step

 Manually import and upgrade Core solution from pipelines
 
 

5.2.2	Approve the pipeline for deployment.
Build Id	Pipeline Name
37384	CD-CrmPlatform-Release


5.2.3	CRM post deployment verification
  Verify workflows are activated from deployment guide (refer 5.16 section)
 
5.3	CDN
Tag	Pipeline Name
SIT_CDN_01Apr2021	CD-CDNContainer-Prd-Release


5.4	Platform APIs
Tag	Pipeline Name
SIT_API_01Apr2021	CD-PlatformAPIs-Prd-Release


5.5	Bot
Tag	Pipeline Name
SIT_Bot_01Apr2021	CD-BotApi-Prd-Release


5.6	Web Apps
Tag	Pipeline Name
SIT_Web_01Apr2021	CD-WebApps-Prd-Release


5.7	B2C Tenant Policy Files
1.	Upload new policy files. Source – Tag - SIT_Web_01Apr2021
a.	B2C_1A_B2B_TrustFrameworkBase_<env>.xml
b.	B2C_1A_B2B_TrustFrameworkExtensions_ <env>.xml
c.	B2C_1A_BO_TrustFrameworkBase_ <env>.xml
d.	B2C_1A_BO_TrustFrameworkExtensions_ <env>.xml
e.	B2C_1A_TrustFrameworkBase_ <env>.xml
f.	B2C_1A_TrustFrameworkExtensions_ <env>.xml
g.	B2C_1A_TrustFrameworkBase_linking_<env>.xml
h.	B2C_1A_TrustFrameworkExtensions_linking_<env>.xml
2.	Please apply any B2C policy customizations selectively done for pre prod environment. Eg: Disabling email verification check on registration.
 
6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
7	Appendix
7.1	 Running Pipeline from Tags
 
