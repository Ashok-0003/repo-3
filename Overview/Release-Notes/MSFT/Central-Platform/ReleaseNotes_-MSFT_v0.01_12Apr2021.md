[ReleaseNotes_ MSFT_v0.01_12Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_12Apr2021-bfed79e4-f10b-4dee-a86a-5d4f96e59fa9.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	Accessibility fixes	2
4	🚀 Deployments	3
1.1	Infrastructure	3
2.2	APIM	3
3.3	Mobile	3
5	💻 Reviewers	4
6	Appendix	5
1.1	Post Deployment Verification	5
2.2	Running Pipeline from Tags	5




Release Note 
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects
None

3	Accessibility fixes
The following issues related to accessibility have been addressed in this build -
ID	Title
34705
NF-Accessibility-IOS iPhone Application-My Account Section
33572
NF-Accessibility-IOS iPhone Application-Applies to All screens in the App-Text Size/ColorContrast /Align content/Heading order
33573
NF-Accessibility-IOS iPhone Application-Modal Dialogue not usable;
34375
NF-Accessibility-Select Plan – billing address forms page- Issues
34367
NF-Accessibility-Registration: (Applies to B2B & B2C)-Validation errors must be specified
34695
NF-Accessibility-IOS iPhone Application-Smart Services - View ALL
33580
NF-Accessibility-IOS iPhone Application-Main Menu -Scrolling: Ensure the content auto scrolls as Focus moves down the screen.
34706
NF-Accessibility-IOS iPhone Application-Main Menu / Home- Scrolling












4	🚀 Deployments
1.1	Infrastructure
Pull Request –  Pull request 6144: Merge TASMU CP to TASMU MSI - 12 Apr 2021 - Repos (azure.com)
Steps: 
1.	Add/update the following parameter files (refer UAT file) - 
Module	Version	Parameter File Name
LogicApp	2016-10-01	logic-<sub>-apps-6dhook-<env>-we-02
BitnamiCkan	2019-06-01	ckan-<sub>-apps-<env>-we-01
2.	CKAN parameter file has new changes for a PostgreSQL server.
3.	Refer Client Id of app registration Central Platform Core APIs in the logic app.
4.	Refer Tenant Id of Azure AD tenant in the logic app.
5.	Refer key Vault kv-<sub>-apps-<env>-we-01 with secret name - CPCoreApis-ClientSecret in the logic app.
6.	Deploy the following resource groups - 
I.	rg-<sub>-apps-int-<env>-we-01
II.	rg-<sub>-apps-ckan-<env>-we-01
7.	Add app settings for the following in   /Scripts/AppConfigurations/settings/<env>/appsettings.json (refer UAT file) - 
I.	CkanSettings
8.	Run CD-AppConfiguration-Master-Release

2.2	APIM
Tag	APIs	Pipeline Name
SIT_APIM_12Apr2021	OrderManagementApi
	CI-APIMConfig-6D-Master-Prd-Build

SIT_APIM_12Apr2021
	OrderManagementApi	CD-APIMConfig-pre-Release


3.3	Mobile
Platform	Build Id	Pipeline Link
Android	39045	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=39045&view=results

iOS	39046	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=39046&view=results

 
5	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
6	Appendix
1.1	Post Deployment Verification
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

2.2	Running Pipeline from Tags
 
