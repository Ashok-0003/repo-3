[ReleaseNotes_ MSFT_v0.01_11May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_11May2021-4337750b-a0e1-494b-9d92-6b0b30ada953.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Fixed Issues	2
4	Accessibility fixes	3
5	⭐ Improvements	3
6	🚀 Deployments	4
6.1	Infrastructure	4
6.2	CRM	5
6.2.1	CRM Pre Deployment Step	5
6.2.2	Deployment	5
6.2.3	CRM Post Deployment Verification	5
Verify workflows are activated from deployment guide (Refer 5.16 section)	5
6.3	CDN	5
6.4	Web Apps	6
6.5	Platform APIs	6
6.6	Mobile	6
7	💻 Reviewers	7
8	Appendix	8
8.1	Post Deployment Verification	8
8.2	Running Pipeline from Tags	8








Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects

The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
33616
NF-Localization- Arabic- Session timeout popup is in English	3 - Medium	2
34146
NF - the header is I sufficient to contain the plan title in Products price plan	3 - Medium	1
34675
FN - My TASMU App - iOS - An error message displayed is not proper when user tries to login using LinkedIn	3 - Medium	1
35776
FN-B2B Marketplace-User logs out of system as soon as it log in	3 - Medium	2
35873
NF-App-Typo is observed for UI message on phone verification screen	4 - Low	2
35874
FN-Portal-Notes for requests does not accept some special symbols where it should be a text field.	3 - Medium	2
35880
FN - B2B - User is not able to search using Name in Orders page	3 - Medium	2

3	🚀 Fixed Issues

The following issues reported are addressed in the current build –
ID	Type	Title	Priority
35777
Issue	FN - Portal - Text values to be changed	1
35781
Issue	Organization verification documents list	1

 
4	Accessibility fixes 
The following issues related to accessibility have been addressed in this build – 
ID 	Title 
35004
NF-Accessibility-IOS iPhone Application-Home Screen
35007
NF-Accessibility-IOS iPhone Application-Home Screen-Form: Complaint / Feedback
35755
NF-Accessibility-IOS iPhone Application-Screen 2: Registration
35756
NF-Accessibility-IOS iPhone Application-Smart Services
5	⭐ Improvements
1.	Email template design updates for CMS related emails
2.	Scale Settings update for AKS, Application Gateways, APIM, Search Service, Cognitive App Service Plan and Cosmos Containers.
 
6	🚀 Deployments
6.1	Infrastructure
Pull Request – https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/6776
Steps: 
1.	Parameter file updates
a.	logic-<sub>-apps-intgbaprl-<env>-we-01
b.	logic-<sub>-apps-intrsl-<env>-we-01
c.	logic-<sub>-apps-intaprv1-<env>-we-01
Please Refer PR : 6783 for the changes required to be incorporated.
2.	Manual Step on cosmos-<sub>-apps-str-<env>-we-01
a.	For all the 5 containers:
i.	botstate
ii.	feedback
iii.	rating
iv.	history
v.	transactionhistory
b.	Update the Scale & Settings to Autoscale and save.
c.	Change the Max RU/s to 6000 and save.
 
 
3.	Deploy 
a.	rg-<sub>-apps-aks-<env>-we-01 (Scale Updates)
b.	rg-<sub>-apps-waf-<env>-we-01 (Scale Updates)
c.	rg-<sub>-shrd-<env>-we-01 (Scale Updates)
d.	rg-<sub>-apps-cog-<env>-we-01 (Scale Updates)
e.	rg-<sub>-apps-int-<env>-we-01
f.	CD-AppConfigurations-Master-Release
4.	Apply the updates on prd as well. 
5.	It is noticed that prd does not have AppServicePlanScale - scale-<sub>-apps-cog-<env>-we-01 (refer pre to update prd)

6.2	CRM
6.2.1	CRM Pre Deployment Step
Manually import processes solution before deployment to higher environments.
 
6.2.2	Deployment
Build Id	Pipeline Name
42313	CD-CrmPlatform-Release


6.2.3	CRM Post Deployment Verification 
Verify workflows are activated from deployment guide (Refer 5.16 section) 

6.3	CDN  
Tag	Pipeline Name
SIT_CDN_11May2021	CD-CDNContainer-Prd-Release


6.4	Web Apps
Tag	Pipeline Name
SIT_Web_11May2021	CD-WebApps-Prd-Release


6.5	Platform APIs
Tag	Pipeline Name
SIT_API_11May2021	CD-PlatformAPIs-Prd-Release


6.6	Mobile
Platform	Build Id	Pipeline Link
Android	42390	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=42390&view=results

iOS	42391	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=42391&view=results

 
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
 
