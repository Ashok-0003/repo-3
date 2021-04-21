[ReleaseNotes_ MSFT_v0.01_20Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_20Apr2021-742c646e-9894-4b1c-b728-406c9c9b7888.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	Accessibility fixes	2
4	⭐ Improvements	2
5	🚀 Deployments	3
5.1	Infrastructure	3
5.2	CDN	4
5.3	Web Apps	4
5.4	Platform APIs	4
5.5	B2C Tenant Policy Files	4
6	Appendix	6
6.1	Post Deployment Verification	6
6.2	Running Pipeline from Tags	6












Release Notes
1	🔧What’s New
New user stories delivered: 
ID	Title	State
14239
As a B2B or B2C user, I should be allowed/disallowed services based on my billing account status so that I can only continue using marketplace services	DOD Ready
2120
Improved robots.txt	DOD Ready

2	🚀 Fixed Defects
The following bugs/Issues reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
33745
NF-Localization-Arabic - B2C/B2B Market Place - unable to add payment method	3 - Medium	1
34157
FN-B2C My TASMU Portal/B2B Marketplace Portal - Safari/Chrome/Edge - Default country code (Qatar) is not set to any mobile number	3 - Medium	2
34653
FN-Portal-User is intermittently getting logged out when it navigates to Profile page from home page and vice versa	2 - High	1
34901
UI-Portal- Status value of the subscription is not aligned properly with its parameter name	4 - Low	3
35036
FN-Portal-404 Not Found error is displayed while verifying mobile number	3 - Medium	1
34619
NF - CKAN items		2
34258
NF - Data Lake storage settings		2
34212
NF - Azure Data Explorer not using Availability zones		2
34215
NF - Private Link/Endpoint to be enabled (Data & AI)		2

3	Accessibility fixes 
None
4	⭐ Improvements
None 
5	🚀 Deployments
5.1	Infrastructure
Pull Request –  Pull request 6340: Merge TASMU CP to TASMU MSI - 20 Apr 2021 - Repos (azure.com)
Steps:
1.	Add parameters http20Enabled, ftpsState, healthCheckPath, webSocketsEnabled to below files:
Module 	Version 	Parameter File Name 
AppServiceManagement	2018-11-01	app-<sub>-apps-arqna-<env>-we-01
AppServiceManagement	2018-11-01	app-<sub>-apps-qna-<env>-we-01
AppServiceManagement	2018-11-01	app-<sub>-apps-bot-<env>-we-01
2.	Update the below files for CKAN changes (refer UAT):
Module	Version	Parameter File Name
NetworkSecurityGroups	2019-11-28	nsg-<sub>-apps-ckndflt-<env>-we-01
VirtualNetwork	2019-11-128	vnet-<sub>-pltf-<env>-we-01
BitnamiCkan	2019-06-01	ckan-<sub>-apps-<env>-we-01
3.	Deploy the following resource groups:
a.	rg-<sub>-apps-cog-<env>-we-01
b.	rg-<sub>-pltf-net-<env>-we-01
c.	rg-<sub>-apps-sec-<env>-we-01
d.	rg-<sub>-apps-ckan-<env>-we-01

4.	Run CD-AppConfigurations-Master-Release
 
5.2	CDN
Tag	Pipeline Name
SIT_CDN_20Apr2021	CD-CDNContainer-Prd-Release


5.3	Web Apps
Tag	Pipeline Name
SIT_Web_20Apr2021	CD-WebApps-Prd-Release


5.4	Platform APIs
Tag	Pipeline Name
SIT_API_20Apr2021	CD-PlatofrmAPIs-Prd-Release


5.5	B2C Tenant Policy Files 
1.	Upload new policy files. Source – Tag - SIT_Web_20Apr2021
1.	B2C_1A_B2B_TrustFrameworkExtensions_PPD
2.	B2C_1A_BO_TrustFrameworkExtensions_PPD
3.	B2C_1A_TrustFrameworkExtensions_PPD
1.	Please apply any B2C policy customizations selectively done for pre prod environment.  
 💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
6	Appendix
6.1	Post Deployment Verification
1.	Function Apps Running 
a.	https://func-cpp-apps-ckan-pre-we-01.azurewebsites.net/ 
b.	https://func-cpp-apps-qnasync-pre-we-01.azurewebsites.net/ 
c.	https://func-cpp-apps-luistra-pre-we-01.azurewebsites.net/ 
d.	https://func-cpp-apps-intbpa-pre-we-01.azurewebsites.net/ 
e.	https://func-cpp-apps-intntf-pre-we-01.azurewebsites.net/ 
f.	https://func-cpp-apps-pt-pre-we-01.azurewebsites.net/ 
2.	Marketplace Portal - http://marketplace.pre.sqcp.qa/en/ 
3.	Bot – Chat with bot on marketplace 
4.	My Tasmu Portal - http://mytasmu.pre.sqcp.qa/en/ 
5.	Account Portal - http://account.pre.sqcp.qa/en/ 
6.	Admin Portal Portal - http://cpadmin.pre.sqcp.qa  (Login screen should come) 
7.	API Config access - https://api.pre.sqcp.qa/config/api/feature 
8.	Open Data Portal - https://opendata.pre.sqcp.qa/

6.2	Running Pipeline from Tags
 
