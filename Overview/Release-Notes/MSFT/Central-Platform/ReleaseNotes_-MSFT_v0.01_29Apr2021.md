[ReleaseNotes_ MSFT_v0.01_29Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_29Apr2021-90dfda13-e8db-4556-ba3a-7f8209b201cd.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Issues	2
3	Accessibility Issues	2
4	⭐ Improvements	3
5	🚀 Deployments	4
5.1	Infrastructure:	4
5.2	CRM	4
5.2.1	CRM Post Deployment Verification	4
5.3	CDN	4
5.4	Web Apps	4
5.5	Platform APIs	4
5.6	Bot	4
5.7	APIM	4
5.8	Mobile	5
6	Appendix	7
6.1	Post Deployment Verification	7
6.2	Running Pipeline from Tags	7







 
Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Issues
The following issues are addressed in the current build –
ID	Title	Severity	Priority
35031
FN - B2B - Product Name is shown thrice in Orders screen	3 - Medium	1
35500
FN-B2B- Profile->Manage login screen is showing Linked account for B2B user	3 - Medium	1
35505
B2B -FN - Hidden password is shown in a case	3 - Medium	3
35595
FN-B2B Marketplace-When organization is registered as Registered in Qatar, it did not ask for any document; and shown as not registered in Qatar on Organization Profile page.	3 - Medium	1
35620
FN-B2B- Error is shown when user uploads more files than required(5 files) on Organization Details page	3 - Medium	3
35039
UI - Alignment is not proper in Reviews section of product description	4 - Low	3
35117
FN-B2B: Incorrect message is displayed for filter on My Account -> Subscription page	3 - Medium	2
35032
FN-Portal-Error is displayed even when correct verificatin code is entered while verifying email address	3 - Medium	1
35521
NF-Security- Web- An adversary can automate the process of submitting publicly accessible forms		4
35159
	NF-Security-Android-Clipboard Paste functionality is not disabled for sensitive text field		4
33745
NF-Localization-Arabic - B2C/B2B Market Place - unable to add payment method	3 - Medium	1
35160
Open Data Portal- Reset Password not possible from the login screen	3 - Medium	2
35112
Open Data Portal - Admin user is not able to add new member to an organization using Email ID	3 - Medium	1

 
3	Accessibility Issues
The following issues are addressed in the current build –
ID	Title	Priority
33572
NF-Accessibility-IOS iPhone Application-Applies to All screens in the App-Text Size/ColorContrast /Align content/Heading order	2
33577
NF-Accessibility-IOS iPhone Application-Main Menu -Menu Modal Dialogue not usable; Fly-out “Menu’’	2
35004
NF-Accessibility-IOS iPhone Application-Home Screen	2
35009
NF-Accessibility-IOS iPhone Application-Home Screen-Form: Modal Dialogue not usable	2

4	⭐ Improvements
CrmPlatform:
•	SMS and Push body length increased to 320 as template for Org and Profile verification.
•	Mapping corrected in workflow for Case.
PlatformAPI:
•	Added SubmitterEmail and BillingSubscriptionId in Get end points for Service and Support requests.
 
5	🚀 Deployments
5.1	Infrastructure: 
Pull Request – https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/6558 
Steps:
1.	Update logic-<sub>-apps-mpsidx-<env>-we-01 for an additional input (Refer UAT file and PR – 6458 in TASMU CP, the changes were already shared in an email by ArunKumar on 28th April, 2021) 
2.	Deploy the rg-<sub>-apps-int-<env>-we-01
3.	Run the CD-AppConfigurations-Master-Release 
5.2	CRM
Build Id	Pipeline Name
41298	CD-CrmPlatform-Release

5.2.1	CRM Post Deployment Verification
  Verify workflows are activated from deployment guide (Refer 5.16 section) 

5.3	CDN
Tag	Pipeline Name
SIT_CDN_29Apr2021	CD-CDNContainer-Prd-Release


5.4	Web Apps
Tag	Pipeline Name
SIT_Web_29Apr2021	CD-WebApps-Prd-Release


5.5	Platform APIs
Tag	Pipeline Name
SIT_API_29Apr2021	CD-PlatformAPIs-Prd-Release


5.6	Bot
Tag	Pipeline Name
SIT_Bot_29Apr2021	CD-BotApi-Prd-Release


 
5.7	APIM 
Tag	APIs	Pipeline Name
SIT_APIM_29Apr2021	MarketplaceCatalogue;Config;Case;cmsdocumentsapi;
	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_29Apr2021	MarketplaceCatalogue;Config;Case;cmsdocumentsapi;	CD-APIMConfig-pre-Release


5.8	Mobile
Platform	Build Id	Pipeline Link
Android	41139	https://dev.azure.com//TASMU%20Central%20Platform/_build/results?buildId=41139&view=results

iOS	41518	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=41518&view=results


 
💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
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
 
