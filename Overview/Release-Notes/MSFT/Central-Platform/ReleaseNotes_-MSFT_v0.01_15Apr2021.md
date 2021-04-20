[ReleaseNotes_ MSFT_v0.01_15Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_15Apr2021-31785bc9-bb10-4638-82f9-141b48408eb0.docx)

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
5.5	Mobile	3
5.6	B2C Tenant App Registration Update	4
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
34145
FN-B2B/B2C- Product/Service Name should be displayed in Orders Page	3 - Medium	1
34508
UI-B2B Marketplace Portal - Login and Register buttons are not displayed when user tries to subscribe to a service as anonymous user	3 - Medium	1
34324
FN-B2B/B2C - About Tasmu: Wrong uppercases and lowercase names	4 - Low	2
33674
FUNC-B2B Marketplace Portal - Supplier Name is not shown on Product Description page	4 - Low	3
34567
FE doesn't behave properly in incognito mode of Chrome browser	3 - Medium	1
34362
FN-Portal-Unable to see the Maximum daily spend option on Subscription Details page	3 - Medium	1
34653
FN-Portal-User is intermittently getting logged out when it navigates to Profile page from home page and vice versa	2 - High	1

3	Accessibility fixes 
The following issues related to accessibility have been addressed in this build - 
ID 	Title 
34363
NF-Accessibility-Contact us-Page enhancement

4	⭐ Improvements
 
5	🚀 Deployments
5.1	Infrastructure
Pull Request – Pull request 6184: Merge TASMU CP to TASMU MSI - 15 Apr 2021 - Repos (azure.com)
Steps:
1.	Update the following parameter files for an additional filter (refer UAT file) - 
Module	Version	Parameter File Name
LogicApp	2016-10-01	logic-<sub>-apps-6dhook-<env>-we-02

2.	Deploy these resource groups:
a.	rg-<sub>-apps-int-<env>-we-01
5.2	CRM
Build Id	Pipeline Name
39142	CD-CrmPlatform-Release


5.2.1	CRM Post Deployment Verification
  Verify workflows are activated from deployment guide (Refer 5.16 section) 

5.3	CDN
Tag	Pipeline Name
SIT_CDN_15Apr2021	CD-CDNContainer-Prd-Release


5.4	Web Apps
Tag	Pipeline Name
SIT_Web_15Apr2021	CD-WebApps-Prd-Release


5.5	Mobile
Platform	Build Id	Pipeline Link
Android	39415	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=39415&view=results

iOS	39416	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=39416&view=results

 
5.6	B2C Tenant App Registration Update
1.	Open Azure Portal and select the Azure B2C Tenant
2.	Navigate to TASMU-Portal app registration.
3.	Select Authentication Tab and add below redirect URIs for marketplace and mytasmu
 https://mytasmu.pre.sqcp.qa/ar/aad-callback/
 https://mytasmu.pre.sqcp.qa/en/aad-callback/
 https://marketplace.pre.sqcp.qa/ar/aad-callback/
 https://marketplace.pre.sqcp.qa/en/aad-callback/
 
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
 
