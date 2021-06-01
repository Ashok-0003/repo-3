[ReleaseNotes_ MSFT_v0.01_31May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_31May2021-fef64fe9-f950-4183-96df-b064b408813a.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Fixed Issues	3
4	Accessibility fixes	4
5	⭐ Improvements	4
6	🚀 Deployments	5
6.1	Infrastructure	5
6.1.1	File Updates	5
6.1.2	Deployments	5
6.1.3	CKAN	6
6.2	CRM	7
6.2.1	Import and Upgrade TASMU_CPM_Core solution form below location:	7
6.2.2	Deployment	7
6.2.3	CRM Post Deployment Verification	7
6.2.4	CRM Email Template Links Update	7
6.2.5	Verify and Update Sector Arabic translation for Cross Sector and Healthcare	7
6.3	CDN	8
6.4	Web Apps	8
6.5	Bot	8
6.5.1	Bot Post Deployment Steps	8
6.6	Developer Portal	10
6.6.1	Pre - Deployment Steps	10
6.6.2	Deployment	10
6.6.3	Post Deployment Step	10
7	💻 Reviewers	11
8	Appendix	12
8.1	Post Deployment Verification	12
8.2	Running Pipeline from Tags	12

Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
36151
FN - B2B - Same KB Article is shown 3 times in chat-bot	3 - Medium	2
36170
FN - Developer Portal -Contact Us is not working	3 - Medium	2
36171
FN - Clicking on MOTC logo on Open Data Portal and Developer Portal does not redirect to MOTC website/Not clickable	3 - Medium	2
36172
UI - Logo for open Data Portal is not clear	3 - Medium	2
36185
UI - Portal - Sector color coding is not correct and some do not have color codes too	3 - Medium	2
36189
FN - B2B - Homepage - 'View All' functionality under Category service list is not working properly	3 - Medium	2
36205
NF- Portal - Arabic - Word wrongly written on Product Name	3 - Medium	2
36225
AA2-Home-Hero banner - image scaling	3 - Medium	2
36233
BB5-Products & Services - Login prompt-Login pop up messaging	3 - Medium	2
36234
BB6-Products & Services - Login prompt-Login pop up messaging	3 - Medium	2
36235
BB7-Products & Services - Login prompt-Login pop up messaging	3 - Medium	2
36236
BB8-Products & Services-Showing All -Pagination not wrapping	3 - Medium	2
36237
BB9-Products & Services - Healthcare > View All-Right side gap when you move/pan the screeen	3 - Medium	2
36239
BB10-Products & Services - Healthcare > View All-Right side gap when you move/pan the screeen	3 - Medium	2
36241
BB12-Products & Services - Billing Address- While filling billing address	3 - Medium	2
36261
NF - Portal - Arabic content on shown on English Portal and vice versa	3 - Medium	2
36303
B2B-Chatbot: Incorrect message after selecting category in products and services	4 - Low	2
36345
NF-Localization-B2B- Cross services translation on "Products and services" page	3 - Medium	2
36346
NF-Localization- B2B- HealthCare Sector missing in the Arabic portal for Filter on Products and services Screen	3 - Medium	2
36356
NF-Localization- Words to be updated on the Product details page	3 - Medium	2
36362
NF - B2B - Portal- My TASMU to be removed from Go To dropdown for English and Arabic	3 - Medium	2
36393
FN-B2B Marketplace-When user visits Order History page, no orders are displayed	3 - Medium	1
36396
FN-B2B Marketplace-Order details are not displayed on Order History Page	3 - Medium	1
35779
FN- B2b- No Details are shown in order screen for cancelled subscription order request	3 - Medium	2
36137
UI -B2B- Thumbnails not shown for Category Services in homepage	3 - Medium	2

3	🚀 Fixed Issues
The following issues reported are addressed in the current build –
ID	Work Item Type	Title	Priority
36176
Issue	UI modification related to P&S	2
36466
Issue	Change the field type of Arabic Answer (FAQ's entity)	2

 
4	⭐ Improvements
 
5	🚀 Deployments
5.1	Infrastructure
PR - Pull request 7158: Merge TASMU CP into TASMU MSI - 31 May 2021 - Repos (azure.com)
5.1.1	File Updates 
1.	Add/Update following parameter files - 
Module	Parameter Files	Action	Properties
LogicApp	logic-<sub>-apps-intprdt-<env>-we-01	Update	Refer PRs: 7134  and 7164 for the changes required to be incorporated.


5.1.2	Deployments
1.	Run the following pipelines – 
a.	CD-rg-<sub>-apps-int-<env>-we-01-Master-Release
b.	CD-AppConfigurations-Master-Release
 
5.1.3	 CKAN
Steps:
1.	Copy latest ckanfiles from stcpdappsckanuatwe01 to st<sub>appsckan<env>we01.
2.	Generate SAS Key for ckanfiles in st<sub>appsckan<env>we01
3.	Run the following commands in all the frontend VMs (ckanfeapps<env>we0<n>) -
a.	sudo vi /opt/bitnami/ckan/venv/src/ckan/ckan/templates/footer.html
Refer below image and on line 24 make this change – href=”https://www.motc.gov.qa/” target=”_blank”
 
b.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme/ckanext/tasmu_theme/public/base
c.	sudo ~/azcopy_linux_amd64_10.10.0/azcopy copy "https://st<sub>appsckan<env>we01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/ckanext/tasmu_theme/public/base/images?<use-sas-key-with-all-permissions>" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal –recursive
d.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme/ckanext/tasmu_theme/public
e.	sudo ~/azcopy_linux_amd64_10.10.0/azcopy copy "https://st<sub>appsckan<env>we01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/ckanext/tasmu_theme/public/tasmu_theme.css?<use-sas-key-with-all-permissions>" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal –recursive
f.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme/ckanext/tasmu_theme/templates
g.	sudo ~/azcopy_linux_amd64_10.10.0/azcopy copy "https://stcpdappsckan<env>we01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/ckanext/tasmu_theme/templates/footer.html?<use-sas-key-with-all-permissions>" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal –recursive
h.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme
i.	sudo python setup.py develop
j.	sudo service bitnami restart

 
5.2	CRM
5.2.1	Import and Upgrade TASMU_CPM_Core solution form below location:
TASMU_CPM_Core
5.2.2	Deployment
Build Id	Pipeline Name
44450	CD-CrmPlatform-Release


5.2.3	CRM Post Deployment Verification
  Verify workflows and business rules are activated from deployment guide (Refer 5.16 section) 
5.2.4	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)
5.2.5	Verify and Update Sector Arabic translation for Cross Sector and Healthcare
Cross Sector - قطاعات متعددة
Healthcare - الرعاية الصحية
 
5.3	CDN
Tag	Pipeline Name
SIT_CDN_31May2021	CD-CDNContainer-Prd-Release


5.4	Web Apps
Tag	Pipeline Name
SIT_Web_31May2021	CD-WebApps-Prd-Release


5.5	Bot
Tag	Pipeline Name
SIT_Bot_31May2021	CD-BotApi-Prd-Release


5.5.1	Bot Post Deployment Steps
Qnamaker English and Arabic – duplicate qna records to be cleaned up for CRM qna instance (tasmubot_CRMKnowledgebase_en_us &tasmubot_CRMKnowledgebase_ar_ar).
1.	Open qnamaker portal : QnA Maker
2.	Select tenant, subscription, and environment – appcog-<sub>-apps-arqna-<env>-we-01 as shown in image (Ref - Image 1 - QNA Instance) and click tasmubot_CRMKnowledgebase_ar_ar highlighted in image below.
3.	Similarly for English appcog-<sub>-apps-qna-<env>-we-01 as shown in image (Ref - Image 1 - QNA Instance) and click tasmubot_CRMKnowledgebase_en_us.
Image 1 - QNA Instance
 
 
4.	There will be two QnA pairs like below image (Ref - Image 2- QNA Pairs). Remove duplicate qna pairs.
Image 2- QNA Pairs
 

5.	After removing all click on save and Train button then click on Publish as shown in image (Ref- Image 3 - Publish QnA).
Image 3 - Publish QnA
 
 
5.6	Developer Portal
5.6.1	 Pre - Deployment Steps
1.	Remove lock for APIM from resource group – rg-<sub>-shrd-<env>-we-01.
2.	Open APIM DevPortal pipeline for Pre Env.
https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=963
3.	Click on Edit, then click on Variables. Below screenshot is for reference.
 
4.	Click on below variables:
o	destEnvUrls 
o	existingEnvUrls  
5.	Update these variables – add comma (,) and append the contact us url: https://marketplace.{env}.sqcp.qa/en/support/contactus
o	destEnvUrls 
	Old value: https://marketplace.pre.sqcp.qa/en/
	New Value: https://marketplace.pre.sqcp.qa/en/,https://marketplace.pre.sqcp.qa/en/support/contactus
o	existingEnvUrls
	Old value: https://marketplace.uat.sqcp.qa/en/
	New value: https://marketplace.uat.sqcp.qa/en/,https://marketplace.uat.sqcp.qa/en/support/contactus
5.6.2	Deployment
Branch	Pipeline Name
Master	CD-APIMDevPortal-rg-cpp-shrd-pre-we-01-Release


5.6.3	Post Deployment Step
1.	Go to apim-<sub>-shrd-<env>-we-01 and publish the developer portal. Refer Step 3 for detailed screenshot.

6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, Sanjeevi Subramani, Rishi Nayak
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
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
2.	Marketplace Portal - https://marketplace.pre.sqcp.qa/en/ 
3.	Bot – Chat with bot on marketplace 
4.	My Tasmu Portal - https://mytasmu.pre.sqcp.qa/en/ 
5.	Account Portal - https://account.pre.sqcp.qa/en/ 
6.	Admin Portal Portal - https://cpadmin.pre.sqcp.qa  (Login screen should come) 
7.	API Config access - https://api.pre.sqcp.qa/config/api/feature 
8.	Open Data Portal - https://opendata.pre.sqcp.qa/

7.2	Running Pipeline from Tags
 
