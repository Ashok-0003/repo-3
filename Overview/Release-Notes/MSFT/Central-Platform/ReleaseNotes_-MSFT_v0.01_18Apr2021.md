[ReleaseNotes_ MSFT_v0.01_18Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_18Apr2021-c445880a-e837-497a-903d-0063234decba.docx)

Contents
1	🔧What’s New	1
2	🚀 Fixed Defects	2
3	Accessibility fixes	2
4	⭐ Improvements	2
5	🚀 Deployments	2
5.1	CDN	2
5.2	Web Apps	3
6	💻 Reviewers	4
7	Appendix	5
7.1	Post Deployment Verification	5
7.2	Running Pipeline from Tags	5




Release Notes
1	🔧What’s New
New user stories delivered: 
ID	Title	State
6961
As a user, I want to view and access all Open Source Projects that are available for TASMU, so that I can use them for my purpose	DOD Ready
6964
As a user, I want to view all published documentation and how to guides available for TASMU, so that I can use them for my purpose	DOD Ready
6965
As a Use Case developer, I want to see guidelines on creating Mobile Apps to be integrated with Central Platform, so that I can develop apps which match the official guidelines	DOD Ready
6966
As a user, I want to view published quick starts content, so that I can use them to build apps	DOD Ready
6967
As a Platform Administrator, I want to publish a list of reusable architecture templates, so that the developer community can use those for their work	DOD Ready
6968
As a developer (subscribed user), I want to access the reusable Virtual Machine deployment templates, so that I can use it for VM Provisioning	DOD Ready

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	State
34509
FN/UI-B2B Marketplace-Password field does not show -Showpassword icon	3 - Medium	2

Note: Payment related scenarios are not verified as there is an issue with Ooredoo payment gateway on Test environment.
3	Accessibility fixes 
The following issues related to accessibility have been addressed in this build - 
ID 	Title 
34363
NF-Accessibility-Contact us-Page enhancement
34517
NF-Accessibility-logged in user: (Applies to B2B & B2C)-collapse icons
34379
NF-B2C-Smart Services – inner page issues

4	⭐ Improvements
None

5	🚀 Deployments
5.1	CDN
Tag	Pipeline Name
SIT_CDN_18Apr2021	CD-CDNContainer-Prd-Release


5.2	Web Apps
Tag	Pipeline Name
SIT_Web_18Apr2021	CD-WebApps-Prd-Release


 
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
 
