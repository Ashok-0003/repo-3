[ReleaseNotes_ MSFT_v0.01_06May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_06May2021-bdda0eaf-d77b-4e7e-8461-f772c23562c1.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	Accessibility fixes	2
4	⭐ Improvements	2
5	🚀 Deployments	3
5.1	Infrastructure	3
5.2	CRM	3
5.2.1	CRM Post Deployment Verification	3
5.3	CDN	3
5.4	Web Apps	3
5.5	Platform APIs	3
5.6	APIM	3
5.7	Mobile	3
5.8	B2C Tenant Policy Files	4
6	💻 Reviewers	5
7	Appendix	6
7.1	Post Deployment Verification	6
7.2	Running Pipeline from Tags	6








Release Notes
1	🔧What’s New
New user stories delivered: None

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
35780
NF-B2B - SMS body received is not proper when a note is added	4 - Low	1
34298
FN-B2C- SignUp/ Registration: Confirm password doesn't match password error message is wrong	3 - Medium	2
34541
FN-Portal-After user logs out, another user is able to access My account page of the user	1 - Critical	1
35030
FN-B2B/B2C- Extra records are created in order screen after successful order placement	3 - Medium	1
35161
FN-Portals-Edge 89: Content is missing on the Home page for registered users	3 - Medium	1
35640
FN - B2B - Expiry date is changed on refresh	4 - Low	3
35645
FN-B2B- Create Service Request option not available in Manage Requests page	3 - Medium	1
35752
FN - APP -Android - Not able to login using valid ID and Password	1 - Critical	1
35518
NF-Security- Android-Activities are exported in the application		4
35519
NF-Security-Android-An adversary can enumerate valid Email IDs		4
3	Accessibility fixes 
None
4	⭐ Improvements
CrmPlatform:
•	Case Pre Update and Case Pre Create Plugins are modified to set the Product name in Case as per subscription.
PlatformAPI:
•	Added ProductName in Get end points for Service and Support requests.

5	🚀 Deployments
5.1	Infrastructure
Pull Request – 
Steps:
5.2	CRM
Build Id	Pipeline Name
41960	CD-CrmPlatform-Release

5.2.1	CRM Post Deployment Verification
  Verify workflows are activated from deployment guide (Refer 5.16 section) 
5.3	CDN
Tag	Pipeline Name
SIT_CDN_06May2021	CD-CDNContainer-Prd-Release


5.4	Web Apps
Tag	Pipeline Name
SIT_Web_06May2021	CD-WebApps-Prd-Release


5.5	Platform APIs
Tag	Pipeline Name
SIT_API_06May2021	CD-PlatformAPIs-Prd-Release


5.6	  APIM 
Tag	APIs	Pipeline Name
SIT_APIM_06May2021	config	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_06May2021	config	CD-APIMConfig-pre-Release


5.7	Mobile
Platform	Build Id	Pipeline Link
Android	41865	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=41865&view=results

iOS	41866	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=41866&view=results


5.8	B2C Tenant Policy Files
1.	Upload new policy files. Source – Tag - SIT_Web_06May2021
a.	B2C_1A_B2B_TrustFrameworkBase_<ENV>.xml
b.	B2C_1A_BO_TrustFrameworkBase_<ENV>.xml
c.	B2C_1A_TrustFrameworkBase_<ENV>.xml

2.	Please apply any B2C policy customizations selectively done for pre prod environment.  
6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
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
2.	Marketplace Portal - http://marketplace.pre.sqcp.qa/en/ 
3.	Bot – Chat with bot on marketplace 
4.	My Tasmu Portal - http://mytasmu.pre.sqcp.qa/en/ 
5.	Account Portal - http://account.pre.sqcp.qa/en/ 
6.	Admin Portal Portal - http://cpadmin.pre.sqcp.qa  (Login screen should come) 
7.	API Config access - https://api.pre.sqcp.qa/config/api/feature 
8.	Open Data Portal - https://opendata.pre.sqcp.qa/

7.2	Running Pipeline from Tags
 
