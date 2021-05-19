# 1 	Purpose
The purpose of this document is to explain the steps to deploy TASMU Dynamics 365 CE Solution. The sections marked as **[Automated]** are automatically deployed through pipeline, those steps are included in this document only for verification after deployment.

[[_TOC_]]

# 2 	Prerequisites
The following are Prerequisites for the deployment.

### 2.1. Dynamics tenant and valid customer service enterprise and field service licenses.
### 2.2. At least 5 GB of database capacity remaining.
### 2.3. 'Dynamics 365 Administrator' Azure AD role for the person provisioning the environment.
### 2.4. Security groups must be created for environment access and licenses assignments similar to below. And the users requiring access must be present in these groups (membership in this groups can be updated after deployment also).

TASMU_AD_CPP_D365_CSE_License (customer service license group)
TASMU_AD_CPP_D365_FS_License (field service license group)
TASMU_AD_CPP_UAT_D365 (environment access group)

### 2.5. Owner permission for the person performing the deployment, on the storage account for setting up [Export to Data Lake](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/137/Dynamics-365-Deployment-Guide?anchor=5.10-configure-export-to-data-lake).

### 2.6. A service account (preferably non interactive) for the purpose of performing automated deployment to Dynamics environment. This account should have access to the target Dynamics environment and must have System Administrator security role within target Dynamics environment (this is not an Azure AD role).

### 2.7. Provision the environment by following this document.
https://docs.microsoft.com/en-us/power-platform/admin/create-environment#create-an-environment-with-a-database

Verify that the environment is provisioned in **West Europe** from the [Export to Data Lake](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/137/Dynamics-365-Deployment-Guide?anchor=5.10-configure-export-to-data-lake) configuration page. If its not, raise a product support ticket to get it moved to West Europe.

Make sure to enter values based on the target environment. Below is sample from UAT. **For production, the type needs to be selected as Production instead of Sandbox**.

![image.png](/.attachments/image-dc21cff4-9dda-440b-8744-c419eff61b80.png)

![image.png](/.attachments/image-7ae998b3-d387-4776-9afe-b35bce0aee46.png)

### 2.8. Azure AD app registrations
The following app registrations are required in the **Azure Active Directory**. Please follow steps mentioned in the **Appendix E - Azure AD App registration** to create app registrations for this purpose.
spn-crm-common-integration-<env>
spn-crm-profile-management-integration-<env>
spn-crm-case-management-integration-<env>

### 2.9 Azure AD B2C app registrations
The following app registrations are required in the **Azure Active Directory B2C**.
**Dynamics365Client<env>**
Refer to the "Dynamics365Client" app registration in the non prod b2c tenant for reference as shown below. API permissions shown below needs to be given and admin consent needs to be given by a Global Admin of the B2C tenant. Keep the client id and secret of this app for later reference.
![image.png](/.attachments/image-263913e3-7020-496c-8bdf-355dc7d7868a.png)

### 2.10 Azure DevOps permissions for creating [service connections](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices), edit the [CD-CrmPlatform-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=111) pipeline, and create/update the target environment in [environments](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_environments).

# 3	Pre-Deployment
### 3.1 Ensure that the deployment pipeline is setup for the target environment
Setup deployment pipeline by following the document below. 
https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/crm-platform?anchor=deployment

### 3.2 Configure Queues [Automated]
The following are the queues to be created. 
1.	Business Operations Queue
2.	ITSM Queue
3.	SQCC Queue
4. Billing Queue
5. Article Approver Queue
6. Internal Email Queue


Follow below steps to create and configure above queues.
1.	Go to https://make.powerapps.com -> Select the right Environment.
2.	Click on Settings on the top right corner “gear” symbol button and then on Advanced Settings button as highlighted below.
 ![image.png](/.attachments/image-383bcdb7-14b7-4cf7-9117-414a2de5eaec.png)

3.	It navigates to below screen, click on Queues as highlighted below.
 ![image.png](/.attachments/image-08e10226-ecbd-4e44-85a4-823fff9acb72.png)

4.	Click on + NEW button as shown below
 ![image.png](/.attachments/image-46e59269-0bc8-433e-90d6-d777d6cddd95.png)

5.	Provide the values as shown below and click on Save button.
 ![image.png](/.attachments/image-f103012d-33c3-463a-ba88-76d6da509c8c.png)

6.	Repeat the above steps to create other queues listed.

### 3.3 Enable Arabic Language in Dynamics
Go to Settings -> Administration -> Languages -> Select Arabic (1025) -> Click on Enable.
This may take several minutes to process.
![image.png](/.attachments/image-de134f29-d71b-4a21-9eae-fbe489aa8615.png)

# 4 Deployment
### 4.1	CRM Solution Import [Automated]

The following are the CRM Customizations and related solutions shown below to be imported sequentially in the order mentioned to the required CRM online instance.

Note: The solution import should be performed by a user with System Administrator or System Customizer role.

1.	TASMU_CPM_WebResources
2.	TASMU_CPM_Core
3.	TASMU_CPM_Plugins
4.	TASMU_CPM_Processes

Please refer to Appendix A for detailed steps to import the CRM Solution.
Note: During import of managed solutions into ETE Organization, make sure to selelct ‘Overwrite Customizations option’ in ‘Import Options’ window as shown below.
 ![image.png](/.attachments/image-cced0f4a-4239-4d3c-9d4b-c0d775e8b1e3.png)

### 4.2	Additional CRM Solution Import
The following are the CRM Customizations and related solutions shown below to be imported sequentially in the order mentioned to the required CRM online instance.

Note: The solution import should be performed by a user with System Administrator or System Customizer role.

1.	TASMU_CPM_SLAs
2.	TASMU_CPM_RoutingRules

Please refer to Appendix A for detailed steps to import the CRM Solution.
Note: During import of managed solutions into ETE Organization, make sure to selelct ‘Overwrite Customizations option’ in ‘Import Options’ window as shown below.
 ![image.png](/.attachments/image-cced0f4a-4239-4d3c-9d4b-c0d775e8b1e3.png)

# 5	Post Deployment Steps
### 5.1	Import Data [Automated]
Import the following data packages using configuration migration tool (refer Appendix B).
•	MasterData.zip

### 5.2	Updating System Settings [Automated]
1.	Sign into Dynamics 365 as System administrator user.
2.	Go to Settings and click on Administration.
3.	Go to System Settings.

### 5.2.1	General Settings
1.	Click on General Tab.
2.	Enter 60 minutes for Duration of inactivity before timeout and 10 min for inactivity warning.
![image.png](/.attachments/image-c865c73c-b7c5-4989-bb15-9bc72e4e674e.png)
 
### 5.2.2	Increase the Note attachment Limit to 20MB (20480 KB)
![image.png](/.attachments/image-3de6efc0-5cf3-4e54-a2de-7da3c57f8552.png)
 
### 5.2.3	Audit Settings
1.	Click on Auditing Tab.
2.	Select Start Auditing and Audit user access from Audit Settings.
3.	Select Common Entities, and Customer Service Entities from Enable Auditing and click on OK.
 ![image.png](/.attachments/image-a68fa140-492e-4317-860d-bc25f3c19548.png)

### 5.3	Enable Connect to Maps for Showing Work Orders in the schedule Board

1.	To enable the Map in the Schedule Board we need to Configure the Below Steps.
![image.png](/.attachments/image-a2a2d7c9-a5ce-4c8f-880d-4330cf17e5dc.png)
  
2.	If “Connected to Maps” is “Yes”, we can view the Work order in the Map view.
![image.png](/.attachments/image-90402d7d-d125-4ddb-90c2-a9614483e90e.png)

### 5.4	Configure customer voice survey on case resolve.

1.	Browse customer voice URL and create new Project.  In Project Template select **Support**.
https://customervoice.microsoft.com/
![image.png](/.attachments/image-e84b8208-422a-45cf-bdbc-f83cc8aed3b0.png)
 
2.	Click on Next -> select the target environment and click on **Select and Close** -> click on **Create**. Below is example for Tasmu Config environment.
![image.png](/.attachments/image-b633e72e-db38-4172-abb3-8c92dfd30451.png)
 
3.	Expand the customization and Click on Personalization and create Case ID Variable.
![image.png](/.attachments/image-956a8ccf-19e7-43be-9ebd-39c4c457fd37.png)
![image.png](/.attachments/image-b7a8f009-926a-462b-aa09-ccab5186c65a.png)
 
4.	Edit the Design Section and add Case ID Variable in the content.

"Hi {{First Name}},This survey is regarding the Case {{ID}} you had with us.We appreciate your business, and we hope you had a great experience with our customer service.Please share your feedback so we can make the experience even better."

![customerVoice_Content.png](/.attachments/customerVoice_Content-ac251c12-58f7-467b-9470-c8f3edca2e35.png)



5. Updated the "Companyname" variable to "TASMU".

![1.CustomerVoice_Signature.png](/.attachments/1.CustomerVoice_Signature-64333eaf-65ae-4dee-b068-2ab4cc4c6946.png)

 
5.	Go to Send tab and click on Edit in Power Automate and Turn on Send Survey Flow.
![image.png](/.attachments/image-0c719ccd-b197-47e4-9572-1f71c2259bc4.png)
![image.png](/.attachments/image-6cfc9a74-53fe-4196-ab28-1ad3778af50c.png)

###5.4.1 Creating Arabic email template
1. Browse customer voice URL https://customervoice.microsoft.com/Pages/ProjectPage.aspx
2. Click on "All Projects", it will show all available projects then double click on the project for which you want to do the update
![AllProjects.PNG](/.attachments/AllProjects-9de1f80a-65e4-4c7d-990a-2bb3c2d16dd1.PNG)
3. Here I am giving example of Test Environment
 Once open the project, then select the survey called "Support Survey - 
 Test". Based on the environment name will be differ. if it is UAT then 
 we have select "Support Survey - UAT", for Dev "Support Survey - Dev".
![Survey.PNG](/.attachments/Survey-dfa60926-0917-4e5b-b319-9a0aa26885ea.PNG)
4. Now click on Send Tab. Then select "Email" in the dropdown.
![Email.PNG](/.attachments/Email-749270de-36e7-4745-9cbc-86c1bf54a66d.PNG)
5. Click on "Template" dropdown then select "Create New", then "Arabic Support Feedback" as a name then click on Add
![CreateNewTemplte.PNG](/.attachments/CreateNewTemplte-bbdec755-0a99-490e-b656-9f0851968ab4.PNG). ![Addingname.PNG](/.attachments/Addingname-30f81b9a-fa81-447e-9c69-de7abca38efe.PNG)
6. Now open the newly created Arabic Support Feedback template using Template dropdown and click on "Source" option in the Editor.Once the editor opens copy the text from Source.txt and paste it in editor. Then clcik on Ok
![selectingArabic.PNG](/.attachments/selectingArabic-1b66fe0b-5c75-4af5-a20d-545532ef52e0.PNG)
[Source.txt](/.attachments/Source-0956b1de-966d-4f2b-81b3-e86d62173d17.txt)![Ok.PNG](/.attachments/Ok-dcf02b24-954f-4088-a79c-23cb83c5c55a.PNG)

###5.4.2 Changing the Trigger Point of Case resolved step.
1 Browse customer voice URL https://customervoice.microsoft.com/Pages/ProjectPage.aspx
2. Click on "All Projects", it will show all available projects then double click on the project for which you want to do the update
![AllProjects.PNG](/.attachments/AllProjects-9de1f80a-65e4-4c7d-990a-2bb3c2d16dd1.PNG)
3. Here I am giving example of Test Environment
 Once open the project, then select the survey called "Support Survey - 
 Test". Based on the environment name will be differ. if it is UAT then 
 we have select "Support Survey - UAT", for Dev "Support Survey - Dev".
![Survey.PNG](/.attachments/Survey-dfa60926-0917-4e5b-b319-9a0aa26885ea.PNG)
4. Now click on Send Tab. Then select "Resend" option in the dropdown. Next in the "Current Flow Run" click on 3dots, Next click on "Edit in Power Automate" option
![EditinPowerutomate.PNG](/.attachments/EditinPowerutomate-623212f3-a32a-4570-afef-81cbc71bde70.PNG)
5. Now "Send a survey when a case is resolved in Dynamics 365" flow is opened in Power Automate. Next select 3dots of "When  case is resolved" step, then select settings option.
 ![trigger.PNG](/.attachments/trigger-faa49a57-9b43-42d2-bffc-62836a873f55.PNG)
6. Once the settings pop up is opened update the "Trigger Conditions" text box with below text

@or(equals(triggerBody()?['statuscode'], 5),equals(triggerBody()?['statuscode'], 1000),equals(triggerBody()?['statuscode'], 923080007))

![triggertext.PNG](/.attachments/triggertext-f2e0d909-fa5a-414d-a8e9-e3991719d693.PNG)

###5.4.3 Updating "Send a survey when a case is resolved in Dynamics 365" flow.
1. Browse customer voice URL https://customervoice.microsoft.com/Pages/ProjectPage.aspx
2. Click on "All Projects", it will show all available projects then double click on the project for which you want to do the update
![AllProjects.PNG](/.attachments/AllProjects-9de1f80a-65e4-4c7d-990a-2bb3c2d16dd1.PNG)
3. Here I am giving example of Test Environment
 Once open the project, then select the survey called "Support Survey - 
 Test". Based on the environment name will be differ. if it is UAT then 
 we have select "Support Survey - UAT", for Dev "Support Survey - Dev".
![Survey.PNG](/.attachments/Survey-dfa60926-0917-4e5b-b319-9a0aa26885ea.PNG)
4. Now click on Send Tab. Then select "Resend" option in the dropdown. Next in the "Current Flow Run" click on 3dots, Next click on "Edit in Power Automate" option
![EditinPowerutomate.PNG](/.attachments/EditinPowerutomate-623212f3-a32a-4570-afef-81cbc71bde70.PNG)
5. Now "Send a survey when a case is resolved in Dynamics 365" flow is opened in Power Automate. Click on "Check if Customer is of type accounts" step. Then in the "If yes" condition, create a new step after "Get primary contact". select "Add an Action" while creating the step
![ifyespr.PNG](/.attachments/ifyespr-99e83814-75ed-49b0-85f6-e0c49ffeace1.PNG)
6. Now select "Condition" as action in the "Choose an operation"
![chooseope.PNG](/.attachments/chooseope-cf9dd3b6-bedd-490b-b72b-223667538d48.PNG)
7. Rename the condition name as "Check Profile Communication Preferred Language", then add dynamic value as "Preferred Communication Language" and select condition as "Preferred Communication Language" is equal to 1025

### 5.5	Enable SLA Flows after deployment

1.	Go to SLA record (Service Management --> Service Level Agreement) and open SLA Record and deactivate.
![image.png](/.attachments/image-079c03df-279d-4391-9ca5-ae273dee4334.png)
 
2.	Inside SLA open SLA Item and Click on Configure.
![image.png](/.attachments/image-7f90a8df-9591-4306-a2eb-65250332fea0.png)
 
3.	It will redirect to the MS Flows click on configure and click on back arrow then turn on flow.
![image.png](/.attachments/image-5153c0e9-d206-42f2-a26f-a140e5effa02.png)
![image.png](/.attachments/image-39a7f78b-8328-42ae-a815-cdac296f5a51.png)

4.	Go back to the SLA record and activate it.

### 5.6	Case Routing Rules

1.	Once the Case Routing rules solution is imported into the target instance, manually update the Queue in the rule items and then activate the Routing rule set.

2. Go to Settings-> Service Management->Routing Rule Sets->Case Routing Rules->Rule Items.

3. Open each row from the rule items grid and update the queue lookup based on the queue name given in the title as shown in the example below.

![BasedonRuleTitleAddtoQueue.png](/.attachments/BasedonRuleTitleAddtoQueue-ff82349b-c0d3-4c4c-9dcc-66a4d8a87f19.png)

4. Once all rule items are updated, activate the routing rule set.

![ActivateRoutingRuleset.png](/.attachments/ActivateRoutingRuleset-eb551604-2034-4601-9d5f-3dd2527c132c.png)
 

### 5.7	Enable Customizable Resolve Case Dialog

1.	Go to Service Management (Change Area) -> Service Configuration Settings -> Select the Style of Resolve Case Dialog box -> Customizable Dialog.
![image.png](/.attachments/image-886c1ec4-f450-40a5-9147-cb26abeb70c9.png)

### 5.8  Move Theme Data
1. We need to make sure that [themes-data.csv](/.attachments/themes-data-359d2f81-f951-48db-96db-736a4566cd46.csv) file is imported in the target environment [Follow the Appendix C - Import record from Excel ]
3. After importing, Custom theme called "Tasmu Theme" will available in the desired environment, we need to manually publish the theme in the respective environment. 

![Publish Theme.png](/.attachments/Publish%20Theme-f0de7009-2bca-4c0c-9fe2-acb0ae52b284.png)

### 5.9  Creating Similar Records Suggestion

1. Go to "Settings"-> "Data Management" -> "Similar Records Suggestions Settings".

![1_SimillarRecordsSettings.png](/.attachments/1_SimillarRecordsSettings-ec245a1f-a02f-40d7-b3f2-3d174ed27ffc.png)

2. Click on  "New" ->Enter "Name" -> "Description" and Save it.

![SimilarCaseRule_1.png](/.attachments/SimilarCaseRule_1-2e32aa5b-9074-4139-b8f1-f2edf2d16fd7.png)

3. Once after it Saved, Go to "Match Fields" tab -> Click on "+" Icon .

![2_SimilarCaseRule_MatchField.png](/.attachments/2_SimilarCaseRule_MatchField-45087fed-3e3f-4351-ada7-712bbe5da8e1.png)

4. Open That Similar Rule  and Go to "Match Field" Tab.-> Click on "New Text Analytic Entity Mapping". After opening the "TEXT ANALYTICS ENTITY MAPPING" , Map the "Entity" and "Field".

![3_CaseText_Analytic_Entity_Mapping.png](/.attachments/3_CaseText_Analytic_Entity_Mapping-25bbf4ba-0f31-4712-9721-2294b8953b9f.png)

![4_SimillarCase_MatchField.png](/.attachments/4_SimillarCase_MatchField-5229d5a0-1097-4347-a108-5c33d02eee10.png)

5. Then "Save and Close" and "Activate" the Similar Rules .

![5_ActivateSimillarRules.png](/.attachments/5_ActivateSimillarRules-c7539edf-441f-4f59-be10-898db28a125f.png)


### 5.10  Add Security Alert Workflow Automation
1. Login into https://portal.azure.com.
2. Go to Security Center.
![image.png](/.attachments/image-30dfa9ae-2eb6-41f9-832e-023daef8b32b.png)
3. Navigate to Workflow automation.
![image.png](/.attachments/image-ac7829c2-780f-47e4-95e3-a42e85eea759.png)
4. Click on Add Workflow automation, new Workflow automation pop up appears.
![image.png](/.attachments/image-fa38e7dd-a014-40c9-ad0a-73ffd57a9a11.png)
5. Enter the details name as alert-rg-cpd-apps-int-<env>-we-01, select the Subscription and Resource group which has the storage blob container which needs to be monitored.
![image.png](/.attachments/image-d0d006ae-6be8-45c1-a2b4-9d56ed66a728.png)
For UAT:
![image.png](/.attachments/image-3807ade8-6968-4353-ac39-de66a88d550b.png)
6. Select Security Center data types as Threat detection alerts.
![image.png](/.attachments/image-58247740-fd57-4408-9ae7-a7fb156e35e3.png)
7. Add 'Potential malware uploaded to a storage blob container' in Alert name contains. In Alert severity select All severities selected.
![image.png](/.attachments/image-37ec16d4-2a77-4a4f-805b-caac5eee1b13.png)
8. In Actions, select the subscription and defender logic app.
![image.png](/.attachments/image-c96bf1b6-3208-4286-a40d-bc9469dab2ac.png)
9. Click on Create.
 
### 5.11 Configure export to data lake and SQL export service
1. Go to https://make.powerapps.com -> select the right environment -> click on Export to data lake -> click on New link to data lake.
![image.png](/.attachments/image-fd0c30f3-6fd0-48b0-83c7-da388a5639e9.png)

2. Select the right resource group, and storage account (contact data and ai team for the storage account name) and click on next.

3. Select all entities in the next screen and finish the setup. More details below.
https://docs.microsoft.com/en-us/powerapps/maker/data-platform/export-to-data-lake#select-and-export-dataverse-table-data-to-azure-data-lake-storage-gen2.

4. Setup SQL export service by following the link below.
https://docs.microsoft.com/en-us/power-platform/admin/replicate-data-microsoft-azure-sql-database

### 5.12 Create and assign security role to Application Users
1. Create the following application users by following "Appendix D - Application User Creation".

| Name | Security Role |
|--|--|
| spn-crm-common-integration-<env> | Common - Integration |
| spn-crm-profile-management-integration-<env> | Profile Management - Integration |
| spn-crm-case-management-integration-<env> | Case Management - Integration |

More details on application users below (only FYI).
https://docs.microsoft.com/en-us/powerapps/developer/data-platform/use-single-tenant-server-server-authentication#application-user-creation

### 5.13 Ensure The Processes are Activated State
Once after the deployment, we need to compare the processes with the "Configuration" environment and make sure that the process are in "Activated" state in the desired environment.

### 5.14 KB Article Image is not populated in Portal
First we need to make sure that the image is loaded by the CMS team in the storage account.
If the Image is loaded in storage account but not populated in portal then we need to open the KB article and open that image in CRM and add manually the web Address (URL). Click on Ok and Update the KB article. 
![image.png](/.attachments/image-8fb163c7-8b85-425e-90b1-20eb9f99c3a4.png)

### 5.15 KB Articles to be created
Two KB articles (One for english and other for Arabic) need to be created in the CRM environment and update the trackingId and trackingId_AR with respective article Ids in environment specific variable section of CD-WebApps-Release and CD-WebApps-Prd-Release (This is already done for pre)

### 5.16 Verify workflows are activated
After deployment, it needs to be verified if workflows are activated or not. If not activated, then follow the below steps: 

In Test Environment below were in Draft state: 
Case: Status Change Notification 

External Note: Notify External Note Created 

Steps to Activate: 
Go to Process -> Check if any Process is in Draft state -> If any of the Process is in Draft state then open that Process -> Solution Layer->Remove Active Customizations->Ok. 
![image.png](/.attachments/image-7c77d5a2-9ff9-4935-a437-e476450bc0ac.png)

Again, close the workflow. Again, re open the workflow and click on "Activate" button. 

![image.png](/.attachments/image-35e05c78-46c8-4e96-bbfb-786a950953ba.png)

### 5.17 Email templates in CRM and Images needs to be uploaded for Prod

####5.17.1 Email Templates images has to be uploaded to CDN for production environment.
####5.17.2 After deployment, English and Arabic templates has to be updated with correct environment specific links for images, hyperlinks and buttons.

Header/Footer Image: Link - https://marketplace.env.sqcp.qa/en/home
Support Button  : Link - https://mytasmu.env.sqcp.qa/en/support/contactus
Terms and Condition :Link https://marketplace.env.sqcp.qa/en/about/tc
Unsubscribe: Link  unsubscribe : https://account.env.sqcp.qa

Note: env-> Specific to environment

for below highlight
![image.png](/.attachments/image-c3aee32d-d21d-40ed-96a6-793e18557b66.png)
![image.png](/.attachments/image-cd44aeb9-e2ac-46ee-a0a2-126417e193e3.png)

Follow the above steps for updating links for below red arrowed buttons, hyper links
For English:
![Template Imgaes Update.png](/.attachments/Template%20Imgaes%20Update-8daeef46-f321-40b1-ae5d-9bceddfe2d1b.png)
For Arabic:![Template_Arabic_Images.png](/.attachments/Template_Arabic_Images-51e26c51-22d5-493c-8865-6af3ae489c38.png)

Need to updates for the below English and Arabic Templates both
Closed Case Acknowledgement
External Note added
Organisation Authentication Change Notification
Organisation Profile Email Verification
Profile Authentication Change Notification
Profile Email Verification Notification
Work Order Booking Created
Work Order Booking Updated
Welcome to SQCP
New Case Acknowledgement


# 6 	Appendix
## Appendix A - Solution Import

Follow the below steps sequentially to import CRM solution.

1.	Go to https://make.powerapps.com -> Select the right Environment.
2.	Go to Solutions and click on Import. 
 ![image.png](/.attachments/image-42393822-ec12-4f28-9966-292ea8e7244e.png)

3.	Select the solution to be imported and click next. 
 ![image.png](/.attachments/image-b843bfab-8687-4be3-9062-6a50bb8e757c.png)
                  
4.	The following screen appears and click on ‘Next’.
![image.png](/.attachments/image-86e27bcb-4725-4454-8c2a-fe465acf88f3.png)
 

5.	Select Overwrite customizations as highlighted and then click on ‘Import’ to begin the solution import process.
![image.png](/.attachments/image-77718b20-1309-435c-b78a-40b534c99b96.png)
 

6.	The below popup opens after clicking on ‘Import’. The green bar shows the progress of the import.
 ![image.png](/.attachments/image-76927e3f-c5c6-44ad-8ab6-38a65522b501.png)

7.	Click on Done. 

8.	Repeat the above steps for all the solutions.

## Appendix B - Data Import using Configuration Migration Utility
Configuration Migration Utility is available as part of Dynamics 365 SDK.
1.	Run the tool by double clicking on the DataMigrationUtility.exe.
2.	Click on Import data and then click on Continue.
 ![image.png](/.attachments/image-9496b01c-0859-4b79-b40b-2595d35176cc.png)

3.	Select the following options, enter the credentials and then login. From the popup window, select the correct Dynamics instance.
 ![image.png](/.attachments/image-c6e6fa0a-1f4c-49fc-a19c-51b91f81c67f.png)

4.	Select the zip file containing the data and click on Import Data.
  ![image.png](/.attachments/image-e3025e03-14c5-42b1-b49e-733f974b6f9e.png)

5.	Verify whether the data is imported by opening the entity from advanced find.

## Appendix C - Import record from Excel


1. Go to Settings > Data Management > Imports.

![1.Go to Import.png](/.attachments/1.Go%20to%20Import-f6618a9a-8a40-4f22-9a27-1dc51f4f9555.png)

2. On the command bar select Import Data > Import Data.

![2.Import Data.png](/.attachments/2.Import%20Data-1cc1a04c-7043-4038-bd44-b93281bea125.png)

3. Browse to the folder where you saved the file that contains the import file. Select the file, and then select Open. Then, select Next.

![BrowseFile_Import.png](/.attachments/BrowseFile_Import-10d5f3b4-214f-4fd8-88cb-0e108e90824a.png)

4. Review File Upload Summary-> Next

![4.ReviewFileUploadSummary.png](/.attachments/4.ReviewFileUploadSummary-e35a0c3a-fc35-45b2-9934-0c1a361b31bf.png)

5. Select Data Map-> Next

![5.SelectDataMap.png](/.attachments/5.SelectDataMap-0169417f-0f51-4cda-9351-4eae59915973.png)

6. We need to map the type of the record . Source Data file -> themes-data . and Microsoft Dynamics 365 Record Types ->Themes -> Click on Next.

![6.MapRecordType.png](/.attachments/6.MapRecordType-1592e184-c063-4e33-bfce-cbc2644ee110.png) 

7. We can Map  (Do Not Modify) Theme ->Theme (Primary Key) as follows . All other fields will automatically mapped from excel. Click Next.

![7.MapThemeFields_I.png](/.attachments/7.MapThemeFields_I-5aaab5a9-adec-45d7-b754-d21430d1d7d8.png)

![10.MapFields_Next.png](/.attachments/10.MapFields_Next-44d18896-9bbc-4499-ac2d-4d1aae946007.png)

8 . Review Mapping Summary-> Click Next

![11.ReviewMappingSummary.png](/.attachments/11.ReviewMappingSummary-2f1e1d29-aa76-4303-abbd-49a662e0c359.png)

9. Review Settings and Import Data->Submit

![12.ReviewSettingImportData.png](/.attachments/12.ReviewSettingImportData-2d330e26-3deb-4b2d-aafd-259034e07c7e.png)

10. Data Submitted for Import->Finish.

![13.DataSubmitted.png](/.attachments/13.DataSubmitted-ea54401e-16b4-448b-8c88-94340c98249e.png)

11. Data Imported from excel and Successfully imported the record.

![14.DataImported.png](/.attachments/14.DataImported-c01af79e-814d-4b6c-b34a-013b127ef7e7.png)

## Appendix D - Application User Creation
To create an unlicensed "application user" in your environment, follow these steps. This application user will be given access to your environment's data on behalf of the end user who is using your application.

1. Navigate to your Dataverse environment (https://[org].crm.dynamics.com).

2. Navigate to Settings > Security > Users.

3. Choose Application Users in the view filter.

4. Select + New.

5. In the Application User form, enter the required information. In the Application ID field, enter the application ID of the app you registered earlier in Azure AD.
![image.png](/.attachments/image-7501a7d9-6a45-4a61-bfdd-b616b75cb7d4.png)

6. After selecting SAVE, if all goes well, the User Name, Application ID URI, Azure AD Object Id, Full Name, and Primary Email fields will auto-populate with correct values where:
  User Name == 'Application Name + Application ID'@TenantID.com
  Full Name == 'Application Name'
  Primary Email == User Name
![image.png](/.attachments/image-4fae397c-5811-4638-b5ca-51cf40f9180f.png)

7. Before exiting the user form, choose MANAGE ROLES and assign a security role to this application user so that the application user can access the desired organization data.

## Appendix E - Azure AD App registration
To create an application registration in Azure AD, follow these steps.

1. Navigate to https://portal.azure.com and switch to the same directory as target dynamics environment.
2. Open Azure Active Directory -> App registrations -> Choose + New registration. 
3. In the Register an application form provide a name for the app, select Accounts in this organizational directory only, and choose Register. A redirect URI is not needed for the purpose of this deployment.
![image.png](/.attachments/image-e90fad09-c63f-4942-99d3-6bccc5fcf653.png)

4. Select Overview in the navigation panel, record the Display name, Application ID, and Directory ID values of the app registration. You will need these in the later steps.

5. In the navigation panel, select Certificates & secrets.

6. Below Client secrets, choose + New client secret to create a secret.

7. In the form, enter a description and select Add. Record the secret string. You will not be able to view the secret again once you leave the current screen.
