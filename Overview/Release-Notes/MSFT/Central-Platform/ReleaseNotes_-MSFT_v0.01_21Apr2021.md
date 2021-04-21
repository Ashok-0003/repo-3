[ReleaseNotes_ MSFT_v0.01_21Apr2021.docx](/.attachments/ReleaseNotes_%20MSFT_v0.01_21Apr2021-c9cefed3-25f6-4149-a959-79a01ed3f99b.docx)

Contents
1	🔧What’s New	2
2	🚀 Fixed Defects	2
3	Accessibility fixes	2
4	⭐ Improvements	2
5	🚀 Deployments	3
5.1	Infrastructure	3
5.2	CDN	4
5.3	Web Apps	4
5.4	Mobile	4
5.5	B2C Tenant Policy Files	4
6	💻 Reviewers	5
7	Appendix	6
7.1	Post Deployment Verification	6
7.2	Running Pipeline from Tags	6










Release Notes
1	🔧What’s New
New user stories delivered: 
User Story Id	Title	State
1362
As a B2C mobile app user, I want to allow/disallow geo tracking feature in TASMU app so that it can be used to show my location and and e-services based on my location sharing preference	DOD Ready
2119
Meta tags in the content published	DOD Ready
2128
404 not found page	DOD Ready
14249
As an end user, I should be able to allowed/disallow services based on my account status.	DOD Ready

2	🚀 Fixed Defects
The following bugs reported in SIT are addressed in the current interim build –
ID	Title	Severity	Priority
34056
FN-My TASMU App - iOS - Payment method can't be saved	3 - Medium	1
34298
FN-B2C- SignUp/ Registration: Confirm password doesn't match password error message is wrong	3 - Medium	2
34509
FN/UI-B2B Marketplace-Password field does not show -Showpassword icon	3 - Medium	2
34981
FN-B2B-B2C-Mobile Unexpected scrolling behavior in chatbot	3 - Medium	2
34992
FN-Portal-UAT-Unable to add Payment Preference	3 - Medium	2
35033
FN-B2B-404 error is shown when click On Terms And Conditions while create an organisation account	3 - Medium	2
35038
FN-B2B-B2C-No results found page is displayed when searching empty string	3 - Medium	2
35040
FN-B2B- Anonymous can't find news using search box	3 - Medium	2

3	Accessibility fixes 
None

4	⭐ Improvements
None


5	🚀 Deployments
5.1	Infrastructure
Pull Request – <None>
Steps:
1.	Review below secrets for payment gateway
a.	PaymentGWSettings-GetPaymentPreferenceServiceURL
b.	PaymentGWSettings-UpdatePaymentPreferenceServiceURL
2.	Check the secrets seeded for any hidden characters. Following website is one way to paste the string online and check for hidden chars - https://www.soscisurvey.de/tools/view-chars.php
 
3.	Remove the hidden characters from the secret string and update the secret value.
4.	Run CD-AppConfigurations-Master-Release to restart the pods.
 
5.2	CDN
Tag	Pipeline Name
SIT_CDN_21Apr2021	CD-CDNContainer-Prd-Release


5.3	Web Apps
Tag	Pipeline Name
SIT_Web_21Apr2021	CD-WebApps-Prd-Release


5.4	Mobile
Platform	Build Id	Pipeline Link
Android	40314	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=40314&view=results

iOS	40315	https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=40315&view=results


5.5	B2C Tenant Policy Files
1.	Upload new policy files. Source – Tag - SIT_Web_21Apr2021
a.	B2C_1A_B2B_PasswordChange_<env>.xml
b.	B2C_1A_B2B_PasswordReset_<env>.xml
c.	B2C_1A_B2B_TrustFrameworkBase_<env>.xml
d.	B2C_1A_B2B_TrustFrameworkExtensions_<env>.xml
e.	B2C_1A_BO_TrustFrameworkBase_<env>.xml
f.	B2C_1A_BO_TrustFrameworkExtensions_<env>.xml
g.	B2C_1A_PasswordChange_<env>.xml
h.	B2C_1A_PasswordReset_<env>.xml
i.	B2C_1A_TrustFrameworkBase_<env>.xml
j.	B2C_1A_TrustFrameworkExtensions_<env>.xml
2.	Please apply any B2C policy customizations selectively done for pre prod environment. Eg: Disabling email verification check on registration.
 
6	💻 Reviewers 
Prepared By	Manvir Kaur, Sumit Gupta, 
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
 
