[ReleaseNotes_ MSFT_v0.01_08Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_08Apr2021-65ca7fca-8ca9-4577-a890-0810aa7e88c6.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	Accessibility fixes	3
4	🚀 Deployments	4
4.1	Infrastructure	4
4.2	CRM	5
4.2.1	CRM post deployment verification	5
4.3	CDN	5
4.4	Web Apps	5
4.5	Platform APIs	5
4.5.1	Update the pipeline.	5
4.5.2	Deploy the pipeline.	6
4.5.3	Update Key Vault Secret	6
4.5.4	Update the App Configuration	6
4.6	APIM	6
4.7	Mobile	6
4.8	Post Deployment Verification	7
5	💻 Reviewers	8
6	Appendix	9
6.1	Running Pipeline from Tags	9



Release Note 
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
34766
FN-My TASMU App- Android - Mobile App crashes when clicked on Subscriptions	1 - Critical	1
34770
FN- App - Account status of the user is shown as blank instead of Suspend	3 - Medium	1
34653
FN-Portal-User is intermittently getting logged out when it navigates to Profile page from home page and vice versa	2 - High	1
34765
FN - Portal - Date of Birth shows today's date	3 - Medium	2
34786
FN-Portal-Safari-Play and Pause button on Hero web does not indicate which button is clicked	4 - Low	2
34840
FN - App - Currency is shown as 'QR' instead of 'QAR'	3 - Medium	4




3	Accessibility fixes
The following issues related to accessibility have been addressed in this build -
ID	Title
33572
NF-Accessibility-IOS iPhone Application-Applies to All screens in the App-Text Size/ColorContrast /Align content/Heading order
33580
NF-Accessibility-IOS iPhone Application-Main Menu -Scrolling: Ensure the content auto scrolls as Focus moves down the screen.
34367
NF-Accessibility-Registration: (Applies to B2B & B2C)-Validation errors must be specified
34375
NF-Accessibility-Select Plan – billing address forms page- Issues
34689
NF-Accessibility-IOS iPhone Application-Chat Bot not accessible to blind users
34690
NF-Accessibility-IOS iPhone Application-Chat Bot -Several Hidden focusable content detected
34691
NF-Accessibility-IOS iPhone Application-Chat Bot -Button; “Find Information”
34692
NF-Accessibility-IOS iPhone Application-Chat Bot -o Buttons for the moment do not link anywhere
34695
NF-Accessibility-IOS iPhone Application-Smart Services - View ALL
34698
NF-Accessibility-IOS iPhone Application-Complaint / Feedback - Gesture control
34705
NF-Accessibility-IOS iPhone Application-My Account Section
34706
NF-Accessibility-IOS iPhone Application-Main Menu / Home- Scrolling
34707
NF-Accessibility-IOS iPhone Application-Main Menu -select languag













4	🚀 Deployments
4.1	Infrastructure
Pull Request –  https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/6020
Steps: 
Changes highlighted with grey are specific to CKAN.
1.	Add/Update/Move below parameter files - 
Module Name	Version	Parameter File Name
FunctionAppCKAN	2021-04-05	func-<sub>-apps-ckan-<env>-we-01
AppServicePlan	2019-08-01	plan-<sub>-apps-ckan-<env>-we-01
LogicApp	2019-05-01	logic-<sub>-apps-purvckan-<env>-we-01
AppServicePlan	2019-08-01	plan-<sub>-apps-int -<env>-we-01
FunctionAppPT	2021-04-05	func-<sub>-apps-pt-<env>-we-01

2.	Add the new CI pipeline to Azure DevOps for CI-FunctionAppCKAN-Master-Build
3.	Add func-<sub>-apps-ckan-<env>-we-01 and plan-<sub>-apps-ckan-<env>-we-01 to deployment of  /DeploymentOrchestration/Environments/<sub>/<env>/rg-<sub>-apps-ckan-<env>-we-01/deploy.json (refer UAT file).
4.	Add the following key vault reference to   /Scripts/AppConfigurations/keyvaultref/<env>/appsettings.json file (refer UAT file) -
a.	CkanSettings:CkanAuthorizationToken
b.	CkanSettings:CkanResourceCreateURL
5.	Deploy the below resource group -
a.	rg-<sub>-apps-ckan-<env>-we-01
b.	rg-<sub>-apps-pt-<env>-we-01
c.	rg-<sub>-apps-int-<env>-we-01

6.	Add access policy in kv-<sub>-apps-<env>-we-01-parameters.json file in Modules\ARM\KeyVault\2021-03-23\Parameters (refer UAT file) for the following - 
Object Id	Secret	Certificate
func-<sub>-apps-pt-<env>-we-01	Get	
func-<sub>-apps-ckan-<env>-we-01	Get	
7.	Deploy rg-<sub>-plft-sec-<env>-we-01
8.	Update role assignment for following resources - 
Identity Name	Type	Target Resource	Role
func-<sub>-apps-pt-<env>-we-01	Function App	acst-<sub>-apps-str-<env>-we-01	App Configuration Store Data Reader
func-<sub>-apps-ckan-<env>-we-01	Function App	acst-<sub>-apps-str-<env>-we-01	App Configuration Store Data Reader

4.2	CRM
Build Id	Pipeline Name
38406	CD-CrmPlatform-Release

4.2.1	CRM post deployment verification
  Verify workflows are activated from deployment guide (refer 5.16 section)

4.3	CDN
Tag	Pipeline Name
SIT_CDN_08Apr2021	CD-CDNContainer-Prd-Release


4.4	Web Apps
Tag	Pipeline Name
SIT_Web_08Apr2021	CD-WebApps-Prd-Release


4.5	Platform APIs
4.5.1	Update the pipeline.
1.	In platform apis, Create a new branch Release/ SIT_API_08Apr2021 from the Tag - SIT_API_08Apr2021
2.	Update the pipeline – pipeline/cd-platformapis-prd-release
3.	Update the pre stage (refer the cd-platformapis-release for correct indentation)
4.	Add below variable in variables section of pre stage:
ckanResourceCreationFunctionAppName: "func-<sub>-apps-ckan-<env>-we-01"
5.	Add below step in steps action at the end.
- task: AzureRmWebAppDeployment@4
                  displayName: Deploy $(sharepointNotifyfunctionApp)
                  inputs:
                    ConnectionType: "AzureRM"
                    azureSubscription: sqcp-ado-spn-pre
                    appType: "functionApp"
                    WebAppName: $(sharepointNotifyfunctionApp)
                    packageForLinux: "$(Pipeline.Workspace)/functionapps/Mcs.TASMU.CMS.Notifications.Functions.zip"

6.	Merge the branch - Release/ SIT_API_08Apr2021 to master.
7.	Deploy the release from the branch - Release/ SIT_API_08Apr2021
4.5.2	Deploy the pipeline.
Branch	Pipeline Name
Release/SIT_API_08Apr2021	CD-PlatformAPIs-Prd-Release


4.5.3	 Update Key Vault Secret
1.	Update the following secret in key vault:
a.	Ckan-ResourceCreateURL
b.	Ckan-ResourceCreationFunctionURL
4.5.4	 Update the App Configuration
Run CD-AppConfigurations-Master-Release to update the configurations and restart the services.

4.6	  APIM 
Tag	APIs	Pipeline Name
SIT_APIM_08Apr2021	cmscontentapi;cmsdocumentsapi;cmsmediaassetsapi;
	CI-APIMConfig-CentralPlatformCore-Master-Prd-Build

SIT_APIM_08Apr2021	cmscontentapi;cmsdocumentsapi;cmsmediaassetsapi;	CD-APIMConfig-pre-Release


4.7	Mobile
Platform	Build Id	Pipeline Link
Android	38354	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=38354&view=results

iOS	38355	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=38355&view=results

 
4.8	Post Deployment Verification
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
 
5	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
6	Appendix
6.1	 Running Pipeline from Tags
 
