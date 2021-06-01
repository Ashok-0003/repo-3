[ReleaseNotes_ MSFT_v0.01_20May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_20May2021-36e1ebc5-105a-460c-8686-68ba4e75cd82.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Fixed Issues	2
4	⭐ Improvements	2
5	🚀 Deployments	3
5.1	Infrastructure	3
5.1.1	File Updates	3
5.1.2	Deployments	3
5.2	CRM	4
5.2.1	Import TASMU_CPM_Core solution manually	4
5.2.2	Deployment	4
5.2.3	CRM Post Deployment Verification	4
5.2.4	CRM Email Template Links Update	4
5.3	CDN	5
5.4	Web Apps	5
5.5	Platform APIs	5
5.6	APIM	5
6	💻 Reviewers	6
7	Appendix	7
7.1	Post Deployment Verification	7
7.2	Running Pipeline from Tags	7



 
Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
35769
FN- Portal - By Selecting any Category from the list, values from all the other mentioned categories become 0.	3 - Medium	2
35961
B2C - Order Subscription - Review and Subscribe: A wrong text for adding another card	3 - Medium	2
35987
NF-B2B Marketplace-My Published Services page is not matching with CEX	3 - Medium	2
36004
FN-B2B- Error is shown to new user on Billing Address screen while placing the order	3 - Medium	2
36029
B2B - 404 Error seen in a case	3 - Medium	2
36045
KB Article Video link not displaying in Portal.	3 - Medium	2

3	🚀 Fixed Issues
The following issues reported are addressed in the current build –
ID	Title	Priority
36003
Add new value to Frequency (Portal)	2

4	⭐ Improvements
Minification of CDN content (HTML, CSS) to improve performance of Azure AD B2C (Login and registration pages).
CRM:
Email template styles updated.
5	🚀 Deployments
5.1	Infrastructure
Pull Request – Pull request 6959: Merge TASMU CP into TASMU MSI - 20 May 2021 - Repos (azure.com)
5.1.1	File Updates
1.	Add/Update the following parameter files (refer UAT files) -
Module	Parameter File	Action	Properties
StorageAccount	st<sub>appsapimt<env>we01
st<sub>appsdiag<env>we01
st<sub>appsint<env>we01
st<sub>appsstr<env>we01
st<sub>shrddiag<env>we01
st<sub>shrd<env>we01	Update
	allowBlobPublicAccess,
minimumTlsVersion,

and diagnostic settings

BitnamiCkan	ckan-<sub>-apps-<env>-we-01	Update	allowBlobPublicAccess,
vmImageReferenceVersion,
storageMinimumTlsVersion

RedisCache	redis-<sub>-apps-str-<env>-we-01	Update	minimumTlsVersion
ContentDeliveryNetworkEndpoint	<env>-cdntasmu	Update	deliveryPolicy,
queryStringCachingBehavior

5.1.2	Deployments
1.	Run the following pipelines - 
a.	CD-rg-<sub>-shrd-mon-<env>-we-01-Master-Release
b.	CD-rg-<sub>-shrd-<env>-we-01-Master-Release 
c.	CD-rg-<sub>-apps-mon-<env>-we-01-Master-Release
d.	CD-rg-<sub>-apps-str-<env>-we-01-Master-Release
e.	CD-rg-<sub>-apps-int-<env>-we-01-Master-Release
f.	CD-rg-<sub>-apps-ckan-<env>-we-01-Master-Release
g.	CD-AppConfigurations-Master-Release
 
5.2	CRM
5.2.1	Import TASMU_CPM_Core solution manually

 
 
5.2.2	Deployment
Build Id	Pipeline Name
43271	CD-CrmPlatform-Release


5.2.3	CRM Post Deployment Verification
  Verify workflows are activated from deployment guide (Refer 5.16 section) 

5.2.4	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)


5.3	CDN 
 Tag 	Pipeline Name 
 SIT_CDN_20May2021	CD-CDNContainer-Prd-Release 


5.4	Web Apps
Tag	Pipeline Name
SIT_Web_20May2021	CD-WebApps-Prd-Release


5.5	Platform APIs
Tag	Pipeline Name
SIT_API_20May2021	CD-PlatformAPIs-Prd-Release


5.6	  APIM 
Tag	APIs	Pipeline Name
SIT_APIM_20May2021	NotificationApi	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_20May2021	NotificationApi	CD-APIMConfig-pre-Release

 
6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
7	Appendix
7.1	Post Deployment Verification
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

7.2	Running Pipeline from Tags
 
