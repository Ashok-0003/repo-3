[ReleaseNotes_ MSFT_v0.01_10May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_10May2021-48f36421-7ab1-4bd2-a7b6-918dbc82b0a1.docx)

Contents
1	🔧What’s New	1
2	🚀 Fixed Issues	2
3	⭐ Improvements	2
4	🚀 Deployments	3
4.1	Infrastructure	3
4.2	Platform APIs	3
4.3	Web Apps	3
4.4	B2C Tenant Policy Files	3
5	💻 Reviewers	4
6	Appendix	5
6.1	Post Deployment Verification	5
6.2	Running Pipeline from Tags	5







 
Release Notes
1	🔧What’s New
New user stories delivered: None
2	🚀 Fixed Issues
The following issues reported are addressed in the current build –
ID	Type	Title	Priority
34213	Issue	NF - Application Gateways non-functional settings	1

3	⭐ Improvements
1.	New node pool for portals in pre-environment
2.	Updated scale settings for portals and apis.
 
4	🚀 Deployments
4.1	Infrastructure
Pull Request – https://dev.azure.com/TASMUCP/TASMU%20MSI/_git/infra/pullrequest/6751
Steps:
1.	Remove lock from rg-cpp-apps-aks-pre-we-01
2.	Delete the agw-cpp-apps-aks-pre-we-01 (to update the zones)
3.	Add the agw-cpp-apps-aks-pre-we-01 (version - 2020-03-26) to Deployment Orchestration
4.	Deploy rg-cpp-apps-aks-pre-we-01
5.	Below role assignment 
Identity Name	Type	Target Resource	Role
mi-cpp-apps-aks-pre-we-01	User Assigned Managed Identity	agw-cpp-apps-aks-prd-we-01	Contributor

6.	Deploy CD-AKS-Release from shared tag
7.	Deploy CD-PlatformAPIs-Prd-Release from shared tag
8.	Deploy CD-WebApps-Prd-Release from shared tag
4.2	Platform APIs
Tag	Pipeline Name
SIT_API_10May2021  (only build and pre stage)	CD-AKS-Release

SIT_API_10May2021	CD-PlatformAPIs-Prd-Release


4.3	Web Apps
Tag	Pipeline Name
SIT_Web_10May2021	CD-WebApps-Prd-Release


4.4	B2C Tenant Policy Files
1.	Upload new policy files. Source – Tag - SIT_Web_10May2021
a.	B2C_1A_B2B_TrustFrameworkBase_<env>.xml
b.	B2C_1A_BO_TrustFrameworkBase_<env>.xml
c.	B2C_1A_TrustFrameworkBase_<env>.xml
2.	Please apply any B2C policy customizations selectively done for pre prod environment.  
5	💻 Reviewers 
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
 
