[ReleaseNotes_ MSFT_v0.01_18May2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_18May2021-1b32e494-674d-48b8-987e-0bbb56071d7a.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	🚀 Fixed Issues	3
4	Accessibility fixes	3
5	⭐ Improvements	3
6	🚀 Deployments	4
6.1	Infrastructure	4
6.1.1	File Updates	4
6.1.2	Deployments	4
6.1.3	CKAN	5
6.2	CRM	7
6.2.1	Import TASMU_CPM_Core solution manually	7
6.2.2	Deployment	7
6.2.3	CRM Post Deployment Verification	7
6.2.4	CRM Email Template Links Update	7
6.3	CDN	8
6.4	Web Apps	8
6.5	Platform APIs	8
6.6	Bot	8
6.7	Mobile	8
6.8	Developer Portal	8
7	💻 Reviewers	9
8	Appendix	10
8.1	Post Deployment Verification	10
8.2	Running Pipeline from Tags	10



Release Notes
1	🔧What’s New
New user stories delivered: 
ID	Title	State
35990
As a B2B/B2C Portal user, I should be able to see the correct Contact details on Contact us page.	DOD Ready

Logo Change for B2B(Marketplace), Account Portal, Open Data Portal and Developer Portal  is implemented
2	🚀 Fixed Defects

The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
33599
FN - Chatbot - Safari/Chrome/Edge - User is unable to initiate a fresh chat, once user has left a message.	3 - Medium	2
35854
FN- B2C My TASMU App- Android- Tool tip doesn't show for a newly registered user	4 - Low	2
35907
FN - MarketPlace Portal - Footer Links are not correct	3 - Medium	2
35931
NF-Work Order Arabic Notifications - (Email/Sms) Status is shown in English for Arabic Profile	3 - Medium	2
35951
FN- iOS-Android - Push Notification does not appear on the ring of the app	4 - Low	2
35953
NF-Localization-B2B- Eligibility message is shown in English for Arabic version	3 - Medium	2
 
3	🚀 Fixed Issues
The following issues reported are addressed in the current build –
ID	Type	Title	Priority
34580
Issue	Enabling of HTTP 2.0	2
35154
Issue	Regression Test Cycle- Co branded Logo Not available	2
4	Accessibility fixes 
The following issues related to accessibility have been addressed in this build – 

ID	Title	Priority
35008
NF-Accessibility-IOS iPhone Application-Home Screen-chatbot	2

5	⭐ Improvements
1.	Supporting more HTML tags for About TASMU and News Articles from CMS end.
 
6	🚀 Deployments
6.1	Infrastructure
Pull Request – Pull request 6869: Merge TASMU CP into TASMU MSI - 17 May 2021 - Repos (azure.com)
6.1.1	File Updates
1.	Update the value for CMS.Function.SupportedHtmlTags key in /Scripts/AppConfigurations/settings/pre/appsettings.json
/Scripts/AppConfigurations/settings/prd/appsettings.json  
Refer the PR Pull request 6832: Adding More HTML Tags - Repos (azure.com)
2.	Update parameter files for enabling http2 (refer this PR) -
a.	agw-<sub>-apps-aks-<env>-we-01
b.	agw-<sub>-apps-api-<env>-we-01
c.	agw-<sub>-apps-ntf-<env>-we-01
d.	agw-<sub>-apps-web-<env>-we-01
6.1.2	Deployments
3.	Enable http2 for agw-<sub>-apps-aks-<env>-we-01 manually from the portal -  
 
4.	Run these pipelines -
a.	CD-AppConfigurations-Master-Release
b.	CD-rg-<sub>-apps-waf-<env>-we-01-Master-Release
 
6.1.3	CKAN
1.	Update the logic app parameters file logic-<sub>-apps-purvckan-<env>-we-01-parameters.json.
Refer to PR: https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra/pullrequest/6828
2.	Run the CD-pipeline: CD-rg-<sub>-apps-ckan-<env>-we-01-Master-Release.
3.	Copy latest ckanfiles from stcpdappsckanuatwe01 to st<sub>appsckan<env>we01. 
4.	Run the following commands in all the 3 Frontend VMs (ckanfeapps<env>we<n>) - 
a.	sudo vi /opt/bitnami/ckan/venv/src/ckan/ckan/templates/footer.html
i.	Change first div class from col-md-8 to col-md-6
ii.	Add new div code for footer logo - 
<div class="col-md-3">
    	{% block footer_logo %}
        	<a class="motctmlogo" href="{{ h.url_for('home.index') }}"><img height="32" 	src="/base/images/ckan-footerlogo-white.png" alt="{{ g.site_title }}" title="{{ 	g.site_title }}" /></a>
    	{% endblock %}
</div>
iii.	Change last div class from col-md-4 to col-md-3

 
b.	sudo vi /opt/bitnami/ckan/venv/src/ckan/ckan/templates/header.html
On line 75 add – height=”50”
 
c.	Generate SAS Key for ckanfiles in st<sub>appsckan<env>we01
d.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme/ckanext/tasmu_theme/public/base
e.	sudo ~/azcopy_linux_amd64_10.10.0/azcopy copy "https://stcpdappsckan<env>we01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/ckanext/tasmu_theme/public/base/images?<use-sas-key-with-all-permissions>" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal –recursive
f.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme/ckanext/tasmu_theme/public
g.	sudo ~/azcopy_linux_amd64_10.10.0/azcopy copy "https://stcpdappsckan<env>we01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/ckanext/tasmu_theme/public/tasmu_theme.css?<use-sas-key-with-all-permissions>" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal --recursive
h.	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme
i.	sudo python setup.py develop
j.	sudo service bitnami restart
 
6.2	CRM
6.2.1	Import TASMU_CPM_Core solution manually

 
 

6.2.2	Deployment
Build Id	Pipeline Name
42930	CD-CrmPlatform-Release


6.2.3	CRM Post Deployment Verification
  Verify workflows are activated from deployment guide (Refer 5.16 section) 

6.2.4	CRM Email Template Links Update
Link to be changed in Email templates in CRM and Images needs to be uploaded for Prod (Refer 5.17 section)
 
6.3	CDN 
Tag 	Pipeline Name 
SIT_CDN_18May2021	CD-CDNContainer-Prd-Release 


6.4	Web Apps
Tag	Pipeline Name
SIT_Web_18May2021	CD-WebApps-Prd-Release


6.5	Platform APIs
Tag	Pipeline Name
SIT_API_18May2021	CD-PlatformAPIs-Prd-Release


6.6	Bot
Tag	Pipeline Name
SIT_Bot_18May2021	CD-BotApi-Prd-Release


6.7	Mobile
Platform	Build Id	Pipeline Link
Android	42763	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=42763&view=results

iOS	42764	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=42764&view=results


6.8	Developer Portal 

Remove lock from rg-<sub>-shrd-<env>-we-01 for apim-<sub>-shrd-<env>-we-01

Branch 	Pipeline Name 
 master	CD-APIMDevPortal-rg-cpp-shrd-pre-we-01-Release 

Go to apim-<sub>-shrd-<env>-we-01 and publish the developer portal. 
Refer Step 3 for detailed screenshot.  
 
7	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta
Company name	Microsoft
Reviewed by 	Ravi Sankar Pillutla, Anil Erkek, Subhajit Chatterjee, Gareeb Navas T M, Mecit Atmaca
Approved by 	Ashwani Sharma

 
8	Appendix
8.1	Post Deployment Verification
Function Apps Running 
https://func-cpp-apps-ckan-pre-we-01.azurewebsites.net/ 
https://func-cpp-apps-qnasync-pre-we-01.azurewebsites.net/ 
https://func-cpp-apps-luistra-pre-we-01.azurewebsites.net/ 
https://func-cpp-apps-intbpa-pre-we-01.azurewebsites.net/ 
https://func-cpp-apps-intntf-pre-we-01.azurewebsites.net/ 
https://func-cpp-apps-pt-pre-we-01.azurewebsites.net/ 
Marketplace Portal - https://marketplace.pre.sqcp.qa/en/ 
Bot – Chat with bot on marketplace 
My Tasmu Portal - https://mytasmu.pre.sqcp.qa/en/ 
Account Portal - https://account.pre.sqcp.qa/en/ 
Admin Portal Portal - https://cpadmin.pre.sqcp.qa  (Login screen should come) 
API Config access - https://api.pre.sqcp.qa/config/api/feature 
Open Data Portal - https://opendata.pre.sqcp.qa/

8.2	Running Pipeline from Tags
 
