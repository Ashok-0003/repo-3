Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	⭐ Improvements	3
4	🚀 Deployments	3
4.1	Infrastructure	3
4.2	CDN	3
4.3	Platform APIs	3
4.4	Bot	3
4.5	Web Apps	4
4.6	Developer Portal	4
4.7	Mobile	4
4.8	B2C Tenant Policy Files	5
5	💻 Reviewers	6
6	Appendix	7
6.1	Running Pipeline from Tags	7








Release Note 
1	🔧What’s New
New user stories delivered: None

List the deferred user stories and ETA:
User Story Id (in MSFT backlog)	Title	Reason of postponement	New ETA
21281	As a developer I want to use Azure purview API to scan the dataset and extract metadata	Work in progress	11-March-2021
8747	As a Consultant I will create custom reporting to monitor Cost Optimization	Awaiting feedbacks to conclude the work	N.A.
8915	As a Consultant I will create 5 pre-defined reports in a Dashboard to allow the Platform Owner to monitor aspects of consumption	Awaiting feedbacks to conclude the work	N.A.
21235		As a Security Architect I'll perform handover sessions for HCF/HCM	Delays in onboarding required members from MSI	11-March-2021

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	State
33750	FN-B2B Marketplace - Portal loading indefinitely when Service Provider with no subscription opens profile-subscription screen	1 – Critical	Resolved
33673	FN-B2C MyTASMU Portal-Safari/Edge - When clicked on Create Support button for an Individual anonymous user, Login page displayed is of Marketplace portal and not MYTASMU Portal	2 - High	Resolved
32960	FN-B2B-Clicking on Terms and Conditions link is not getting redirected to Terms and Conditions page.	3 - Medium	Resolved
33248	NF-Localization-Arabic - B2C Market Place - Text not translated in News tab	3 - Medium	Resolved
33249	NF-Localization-Arabic - B2C Market Place - Registration page header is in English 	3 - Medium	Resolved
33252	NF-Localization-Arabic - My Account- Guide text missing in the profile page	3 - Medium	Resolved
33254	NF-Localization-Arabic - My Account- text not translated in payment preferences page	3 - Medium	Resolved
33543	FUNC - B2C - My TASMU Portal - Arabic - Business Owner isn’t able to enter Arabic names in Company Name field	3 - Medium	Resolved
33547	NF-Localization-Arabic - B2C Market Place - Reset Password page is in English	3 - Medium	Resolved
33604	FN-B2B- User is unable to update and save Organizational details	3 - Medium	Resolved
33616	NF-Localization- Arabic- Session timeout popup is in English	3 - Medium	Resolved
33689	NF-Localization-Arabic - B2C/B2B Market Place - unable to upload PNG file to support tickets	3 - Medium	Resolved
33745	NF-Localization-Arabic - B2C/B2B Market Place - unable to add payment method	3 - Medium	Resolved
33034	NF-Localization-Arabic - B2B Market Place - Text not translated in News tab	3 - Medium	Resolved
33035	NF-Localization-Arabic - B2B Market Place - Product Detail -subscribe button not translated 	3 - Medium	Resolved
33039	NF-Localization-Arabic - B2B Market Place - Registration- Verification code label alignment 	3 - Medium	Resolved
33043	FN - B2C My TASMU Portal - Edge - Add Account page is showing Marketplace logo	4 - Low	Resolved
33067	NF-Localization-Arabic - B2B Market Place - My Account- English Add account page 	3 - Medium	Resolved
33068	NF-Localization-Arabic - B2B Market Place - My Account- English Change Password page	3 - Medium	Resolved
33069	NF-Localization-Arabic - My Account- fields alignment in Profile page	3 - Medium	Resolved

Known Issue: Unable to log in with Facebook/LinkedIn accounts. 
Informed AbdelRahman from Malomatia, as Social IDP has been blocked. Not a code issue.
3	⭐ Improvements
CMS: Batching has been implemented for consuming Get Changes API (OOTB SharePoint REST API), so that all the changes happening in SPO will be tracked in more efficient way.

4	🚀 Deployments
4.1	Infrastructure
Pull Request - https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/4956
1.	Update srch-<sub>-apps-arcog-<env>-we-01 for replica changes
2.	Update srch-<sub>-apps-cog-<env>-we-01 for replica changes if not already done.
3.	Redeploy rg-<sub>-apps-cog-<env>-we-01
4.	Delete the default products starter and unlimited from APIM – Refer 6.1.4
5.	Update App Configurations for pre and run CD-AppConfigurations-Master-Release

4.2	CDN
Tag	Pipeline Name
SIT_CDN_04Mar2021	CD-CDNContainer-Prd-Release


4.3	Platform APIs
Tag	Pipeline Name
SIT_API_04Mar2021	CD-PlatformAPIs-Prd-Release


4.4	Bot
Tag	Pipeline Name
SIT_Bot_04Mar2021	CD-BotApi-Prd-Release


4.4.1. After the above bot pipeline deployment must trigger logic-<sub>-apps-qnacopy-<env>-we-01 once – so that it will trigger the Luis trainer function app to train the updated luis deployment changes.
Refer screenshot below for triggering the qnacopy logic app => open app in azure portal => click on Development Tools => Logic app designer => Run.
 
4.5	Web Apps
Branch	Pipeline Name
release/sit_web_04mar2021	CD-WebApps-Prd-Release


4.6	Developer Portal
Add/Update the pipeline variables:
Variable Name	Variable Value 	Description
existingEnvUrls	https://marketplace.uat.sqcp.qa/en/
Marketplace portal url of the source environment
destEnvUrls	https://marketplace.pre.sqcp.qa/en/
Marketplace portal url of the target/current environment
deployTo	crosssubscrp	Constant value – it will be ‘samesubscrp’ if both the source and destination apim are in same subscription, if it is under different subscription then ‘crosssubscrp’

Branch	Pipeline Name
master	CD-APIMDevPortal-rg-cpp-shrd-pre-we-01-Release


Go to apim-<sub>-shrd-<env>-we-01 and publish the developer portal.
Refer Step 3 for detailed screenshot. 
4.7	Mobile
Important Note: Updates for the Build agents is required to build and distribute the mobile apps. Please follow the steps from this link. This update is mainly for Android builds.
Platform	Build Id	Pipeline Name
Android	31845	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=31845&view=results

iOS	31846	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=31846&view=results


4.8	B2C Tenant Policy Files
1.	Upload new policy files from PPD folder. Refer Tag - SIT_CDN_04Mar2021 as source.
2.	Please apply any B2C policy customizations selectively done for pre prod environment. Eg: Disabling email verification check on registration.
 
5	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
6	Appendix
6.1	 Running Pipeline from Tags