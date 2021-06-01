[ReleaseNotes_ MSFT_v0.01_25May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_25May2021-13352910-78d4-408a-9428-d1dea52dcdd5.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	⭐ Improvements	3
4	🚀 Deployments	4
4.1	Infrastructure	4
4.1.1	File Updates	4
4.1.2	Deployments	4
4.2	CRM	5
4.2.1	Import TASMU_CPM_Core solution manually	5
4.2.2	Deployment	5
4.2.3	CRM Post Deployment Verification	5
4.2.4	CRM Email Template Links Update	5
4.2.5	Survey Email Templates	5
4.3	Web Apps	6
4.4	Platform APIs	6
4.5	Mobile	6
5	💻 Reviewers	7
6	Appendix	8
6.1	Post Deployment Verification	8
6.2	Running Pipeline from Tags	8

 
Release Notes
1	🔧What’s New
New user stories delivered: 
ID	Title	State
35905
As a developer, I need to update the UX of CMS related email templates so that it is in-lined with latest approved email template design	DOD Ready
35967
As a developer, I want to update the UX of email templates for CRM automated emails so that it is in-line with latest approved email template design	DOD Ready
36062
As a developer, I need to create About TASMU HTML pages which were approved so that additional formatting options can be utilized	DOD Ready
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
35912
FN-Portal-Arabic-While selecting country in Billing Address, countries are not alphabetically sorted	4 - Low	2
35970
B2C - Order Subscription - Field 'Zone' is not mandatory for 1st try of subscription at service	3 - Medium	2
36017
NF-Localization-B2B- About TASMU is not fully in Arabic in the Menu of home page	3 - Medium	2
36079
NF- Localization- B2B - Title of section not correctly written	4 - Low	2
36085
NF-Localization- B2B- On Home page View all is in English for Arabic version	3 - Medium	2

 
3	⭐ Improvements
1.	Email template design updates for CMS related emails
2.	About TASMU Links update in portal.
a.	 Team is removed.
b.	Enabling digitalization and leadership is added.
               [Please clear the local storage cache while testing]
3.	Remove multiple API calls during configure order screen.
4.	Updated SaveOrder call to pass English Values instead of GUID’s used by ITSM.
 
4	🚀 Deployments
4.1	Infrastructure
Pull Request – Pull request 7031: Merge TASMU CP into TASMU MSI - 25 May 2021 - Repos (azure.com)
4.1.1	File Updates
1.	Add/Update following parameter files - 
Module	Parameter Files	Action	Properties
LogicApp	logic-<sub>-apps-intgbaprl-<env>-we-01
logic-<sub>-apps-intrsl-<env>-we-01
logic-<sub>-apps-intaprv1-<env>-we-01
	Update	Refer PRs : 6984 ,  7003  and 7016 for the changes required to be incorporated.

StorageAccount	st<sub>glocacmwe01

(refer cpd file)	Update
	allowBlobPublicAccess,
minimumTlsVersion,
blobContainers,
and diagnostic settings

4.1.2	Deployments
1.	Run the following pipelines - 
a.	CD-rg-<sub>-glob-acm-we-01-Master-Release
b.	CD-rg-<sub>-apps-int-<env>-we-01-Master-Release
c.	CD-AppConfigurations-Master-Release
 
4.2	CRM
4.2.1	Import TASMU_CPM_Core solution manually

 
 
4.2.2	Deployment
Build Id	Pipeline Name
43699	CD-CrmPlatform-Release


4.2.3	CRM Post Deployment Verification
  Verify workflows and business rules are activated from deployment guide (Refer 5.16 section) 

4.2.4	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)
4.2.5	Survey Email Templates
The manual steps will be informed in call.
 
4.3	Web Apps
Tag	Pipeline Name
SIT_Web_25May2021	CD-WebApps-Prd-Release


4.4	Platform APIs
Tag	Pipeline Name
SIT_API_25May2021	CD-PlatformAPIs-Prd-Release


4.5	Mobile
Platform	Build Id	Pipeline Link
Android	43311	Pipelines - Run 20210520.3 (azure.com)

iOS	43312	Pipelines - Run 20210520.3 (azure.com)


 
5	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
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
2.	Marketplace Portal - https://marketplace.pre.sqcp.qa/en/ 
3.	Bot – Chat with bot on marketplace 
4.	My Tasmu Portal - https://mytasmu.pre.sqcp.qa/en/ 
5.	Account Portal - https://account.pre.sqcp.qa/en/ 
6.	Admin Portal Portal - https://cpadmin.pre.sqcp.qa  (Login screen should come) 
7.	API Config access - https://api.pre.sqcp.qa/config/api/feature 
8.	Open Data Portal - https://opendata.pre.sqcp.qa/

6.2	Running Pipeline from Tags
 
