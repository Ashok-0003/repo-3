[ReleaseNotes_ MSFT_v0.01_25Feb2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_25Feb2021-1699f57c-a9ee-42a4-bcb6-4bb351a25688.docx)

**Release Note**  

**_🔧1.0 What’s New (New delivered user stories)_**
List out the new user stories that you delivered.
None

**List the deferred user stories and ETA:**
User Story Id (in MSFT backlog)	Title	Reason of postponement	New ETA
21281	As a developer I want to use Azure purview API to scan the dataset and extract metadata	Work in progress	4-March-2021
8747	As a Consultant I will create custom reporting to monitor Cost Optimization	Awaiting feedbacks to conclude the work	N.A.
8915	As a Consultant I will create 5 pre-defined reports in a Dashboard to allow the Platform Owner to monitor aspects of consumption	Awaiting feedbacks to conclude the work	N.A.
21235		As a Security Architect I'll perform handover sessions for HCF/HCM	Delays in onboarding required members from MSI	11-March-2021

**_🚀 2.0 Fixed Defects_**

The following 15 bugs (portal related) reported in SIT are addressed in the current interim build –
ID	Title	Severity	State
32965
FN - My TASMU Portal - Sf - Error is displayed when Business owner tries to visit a page with no records	3 - Medium	Resolved
32966
FN-B2C-Support request search is not working as expected, when searched by invalid inputs no message is displayed	3 - Medium	Resolved
33005
NF-Localization-Arabic - B2B Market Place - Home Page tabs are not translated	3 - Medium	Resolved
33007
NF-Localization-Arabic - B2B Market Place - Chatbot welcome message not translated	3 - Medium	Resolved
33034
NF-Localization-Arabic - B2B Market Place - Text not translated in News tab	3 - Medium	Resolved
33041
NF-Localization-Arabic - B2B Market Place - Text not translated in Configure plan page	3 - Medium	Resolved
33045
NF-Localization-Arabic - B2B Market Place - Products- duplicate fields in the billing address tab	3 - Medium	Resolved
33046
NF-Localization-Arabic - B2B Market Place - Homepage- Wrong translation in Smart Services by Sector section	3 - Medium	Resolved
33072
NF-Localization-Arabic - B2B Market Place - Contact Us- overlap in the attachment box	3 - Medium	Resolved
33119
FN - B2B Marketplace Portal - Chrome- Subscription not possible for Free service/product	2 - High	Resolved
33171
NF-Localization-Arabic - B2B Market Place - Contact Us- wrong Arabic Translation	4 - Low	Resolved
33173
NF-Localization-Arabic - Market Place - Home tab translation	3 - Medium	Resolved
33174
NF-Localization-Arabic - B2B Market Place - My Account- Preferred method of contact field is in English	3 - Medium	Resolved
33175
NF-Localization-Arabic - B2B Market Place - My Account- drop menus in the address tab	3 - Medium	Resolved
33257
NF-Localization-Arabic - B2C Market Place - Chatbot welcome message not translated	3 - Medium	Resolved

Note: 
Mobile build is not included as part of this release. As communicated, it will be shared on Sunday 28 February 2021.

⭐ 3.0 Improvements
List out all improvements that you've made to your product.
None

_**🚀 4.0 Deployments**_

4.1 Infrastructure
Pull Request - https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/4743
UAT can be taken as reference.
1.	Add Action Group Module (update the variables and new pipeline in ADO according to MSI)
2.	Add Action Group parameter file for pre and deploy the resource to rg-<sub>-apps-mon-<env>-we-01 
3.	Update the App Service Management to include Action Group -  appcog-<sub>-apps-arqna-<env>-we-01 ,  appcog-<sub>-apps-bot-<env>-we-01 ,  appcog-<sub>-apps-qna-<env>-we-01 
4.	Redeploy rg-<sub>-apps-cog-<env>-we-01
5.	Add private end points, follow steps 5.1, 5.2 and 5.3 of UAT-Apps-Workload-Deployment-Steps
6.	Update cosmos parameter file - cosmos-<sub>-apps-str-<env>-we-01 for private end point and diagnostic settings
7.	Redeploy rg-<sub>-apps-str-<env>-we-01 
8.	Update logic app - logic-<sub>-apps-intsubs-<env>-we-01 
9.	Redeploy rg-<sub>-apps-int-<env>-we-01 
10.	Deploy the App Configurations for pre (CD-AppConfigurations-Master-Release)

4.2 CDN
Tag	Pipeline Name
SIT_CDN_25Feb2021	CD-CDNContainer-Prd-Release


4.3 Platform APIs
Tag	Pipeline Name
SIT_API_25Feb2021	CD-PlatformAPIs-Prd-Release


4.4 Bot
Tag	Pipeline Name
SIT_Bot_25Feb2021	CD-BotApi-Prd-Release


4.5 Web Apps
Tag	Pipeline Name
SIT_Web_25Feb2021	CD-WebApps-Prd-Release


4.6 APIM 
APIs	Pipeline Name
Profile	CI-APIMConfig-Prd-Master-Build

Profile	CD-APIMConfig-pre-Release


4.7CRM
Pipeline Name
CD-CrmPlatform-Release



_**💻 5.0 Reviewers**_ 

Prepared By	Manvir Kaur, Sumit Gupta, Sutan Dan
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Abhishek Ghosh, Subhajit Chatterjee, Gareeb Navas T M
Approved by 	Ashwani Sharma


 
6.0 Appendix
6.1 Running Pipeline from Tags
