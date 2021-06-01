[ReleaseNotes_ MSFT_v0.01_13May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_13May2021-b7888b55-a600-4026-b7f0-18463b72f040.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Fixed Issues	2
4	Accessibility fixes	2
5	⭐ Improvements	2
6	🚀 Deployments	3
6.1	CRM	3
6.1.1	CRM Post Deployment Verification	3
6.2	CDN	3
6.3	Web Apps	3
6.4	Platform APIs	3
7	💻 Reviewers	4
8	Appendix	5
8.1	Post Deployment Verification	5
8.2	Running Pipeline from Tags	5








Release Notes
1	🔧What’s New
New user stories delivered: None
Logo Rebranding is done for B2B(Marketplace) and Account Portal.

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
35912
FN-Portal-Arabic-While selecting country in Billing Address, countries are not alphabetically sorted	4 - Low	2
35913
NF-Arabic-On order successful page, "Pending" Status is displayed in english, when language selected is Arabic	3 - Medium	2
35932
Main Image source is mapped with thumbnail image	3 - Medium	2
35931
NF-Work Order Arabic Notifications - (Email/Sms) Status is shown in English for Arabic Profile		
3	🚀 Fixed Issues
The following issues reported are addressed in the current build –
ID	Type	Title	Priority
	Issue		
4	Accessibility fixes 
The following issues related to accessibility have been addressed in this build - 
ID 	Title 
	
 	
5	⭐ Improvements
 
6	🚀 Deployments
6.1	CRM
Build Id	Pipeline Name
42658	CD-CrmPlatform-Release

6.1.1	CRM Post Deployment Verification
•	  Verify workflows are activated from deployment guide (Refer 5.16 section) 
6.1.2      CRM Email Templates Links update
•	Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)

6.2	CDN
Tag	Pipeline Name
SIT_CDN_13May2021	CD-CDNContainer-Prd-Release


6.3	Web Apps
Tag	Pipeline Name
SIT_Web_13May2021	CD-WebApps-Prd-Release


6.4	Platform APIs
Tag	Pipeline Name
SIT_API_13May2021	CD-PlatformAPIs-Prd-Release


 
7	💻 Reviewers
 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
8	Appendix
8.1	Post Deployment Verification
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

8.2	Running Pipeline from Tags
 
