[ReleaseNotes_ MSFT_v0.01_28May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_28May2021-764723bd-ffc6-4a2f-a4a3-f4cb49484eb3.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Deployments	4
3.1	CRM	4
3.1.1	Import TASMU_CPM_Core solution manually	4
3.1.2	Deployment	4
3.1.3	CRM Post Deployment Verification	4
3.1.4	CRM Email Template Links Update	4
3.2	Web Apps	4
4	💻 Reviewers	5
5	Appendix	6
5.1	Post Deployment Verification	6
5.2	Running Pipeline from Tags	6

 
Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
36158
FN-B2B: Support request email doesn't contain description of support request	3 - Medium	2
36161
FN-B2B: Profile subcriptions search is not working	3 - Medium	2
36187
NF - Portal - Sentence to be removed from Products & Services Category list on homepage	3 - Medium	2
36224
AA1-Home-Hero banner - copy alignment	3 - Medium	2
36225
AA2-Home-Hero banner - image scaling	3 - Medium	2
36226
AA3-Home- Menu	3 - Medium	2
36227
AA4-Home-- Text alignment	3 - Medium	2
36228
AA5-Home- Double animation	3 - Medium	2
36229
BB1-Products & Services - breadcrumb-Broken breadcrumb	3 - Medium	2
36230
BB2-Products & Services - Description title-Description sub-heading has a highlight box around when click near or on term	3 - Medium	2
36231
BB3-Products & Services - Description title-Description sub-heading has a highlight box around when click near or on term	3 - Medium	2
36232
BB4-Products & Services - Description title-Description sub-heading has a highlight box around when click near or on term	3 - Medium	2
36240
BB11-Products & Services - Filters Icon- Products & Services icon	3 - Medium	2
36242
CC1-News - Most Popular-Vertical alignment of Share icon	3 - Medium	2
36243
CC2-News - Most Popular-Vertical alignment of Share icon	3 - Medium	2
36244
CC3-News - Most Popular-Vertical alignment of Share icon	3 - Medium	2
36245
CC4-News - Most Popular-Vertical alignment of Share icon	3 - Medium	2
36246
CC5-News - Most Popular-Vertical alignment of Share icon	3 - Medium	2
36247
DD1-Our Vision-Title should be 'Our Vision' not 'Vision Mission' within navigation	3 - Medium	2
36248
DD2-Our Vision-Title should be 'Our Vision' not 'Vision Mission' within navigation	3 - Medium	2
36249
DD3-Our Vision-Title should be 'Our Vision' not 'Vision Mission' within navigation	3 - Medium	2
36250
DD5-Our Vision-Page nav icon missing title	3 - Medium	2
36251
DD4-Our Vision-Page nav icon missing title	3 - Medium	2
36252
DD6/7/8-About Tasmu - The Team-No content- remove section	3 - Medium	2
36253
DD9/10-About Tasmu -Cropped in page menu	3 - Medium	2
36254
EE1/2-Contact Us - button alignment-Submit and Cancel button alignment	3 - Medium	2
36255
EE3/4-Knowledge Base - article-Image not scaling for responsive view	3 - Medium	2
36256
EE5/6/7-Contact Us - Cancel-Cancel button redirect	3 - Medium	2
36263
FN-B2B Marketplace-When user is not subscribed to a product, Review page should show a message saying "You are not subscribed to this product, the review function only works for subscribed users."	3 - Medium	2
36264
FN-B2B Marketplace- Search bar needs exact word to fetch search results	3 - Medium	2

 
3	🚀 Deployments
3.1	CRM
3.1.1	Import TASMU_CPM_Core solution manually 
  
  

3.1.2	Deployment
Build Id	Pipeline Name
44133	CD-CrmPlatform-Release


3.1.3	CRM Post Deployment Verification
  Verify workflows and business rules are activated from deployment guide (Refer 5.16 section) 
3.1.4	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)

3.2	Web Apps
Tag	Pipeline Name
SIT_Web_28May2021	CD-WebApps-Prd-Release


4	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M
Approved by 	Ashwani Sharma

 
5	Appendix
5.1	Post Deployment Verification
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

5.2	Running Pipeline from Tags
 
