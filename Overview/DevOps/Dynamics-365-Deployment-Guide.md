# 1 	Purpose
The purpose of this document is to explain the steps to deploy TASMU Dynamics 365 CE Solution.

# 1 	Prerequisites
The following are Prerequisites for the deployment.
- Dynamics tenant and valid customer service enterprise and field service licenses.
- At least 5 GB of database capacity remaining.
- 'Dynamics 365 Administrator' Azure AD role for the person provisioning the environment.
- Security groups must be created for environment access and licenses assignments similar to below. And the users requiring access must be present in these groups (membership in this groups can be updated after deployment also).
TASMU_AD_CPP_D365_CSE_License (customer service license group)
TASMU_AD_CPP_D365_FS_License (field service license group)
TASMU_AD_CPP_UAT_D365 (environment access group)

- A service account (preferably non interactive) for the purpose of performing automated deployment to Dynamics environment. This account should have access to the target Dynamics environment and must have System Administrator security role within target Dynamics environment (this is not an Azure AD role).

- Provision the environment by following this document.
https://docs.microsoft.com/en-us/power-platform/admin/create-environment#create-an-environment-with-a-database

- Azure AD app registrations
The following app registrations are required in the **Azure Active Directory**. Please follow steps mentioned in the **Appendix E - Azure AD App registration** to create app registrations for this purpose.
spn-crm-common-integration-<env>
spn-crm-profile-management-integration-<env>
spn-crm-case-management-integration-<env>

- Azure AD B2C app registrations
The following app registrations are required in the **Azure Active Directory B2C**.
**Dynamics365Client<env>**
Refer to the "Dynamics365Client" app registration in the non prod b2c tenant for reference as shown below. API permissions shown below needs to be given and admin consent needs to be given by a Global Admin of the B2C tenant. Keep the client id and secret of this app for later reference.
![image.png](/.attachments/image-263913e3-7020-496c-8bdf-355dc7d7868a.png)

- Setup deployment pipelines by following the document below. This step requires Azure DevOps permissions to create new **service connections** as well as permission to **edit the pipeline(s)** mentioned in the document below.
https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/crm-platform?anchor=deployment

## 1	Pre-Deployment
### 1.1 Configure Queues [Automated]
The following are the queues to be created. 
1.	Business Operations Queue
2.	ITSM Queue
3.	SQCC Queue

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


### 1.2 Assign security roles to the teams
 
1.	Open the team crated in the previous step, click on MANAGE ROLES ribbon button and assign security role ‘Tasmu Article Approver’  to the team and click on OK button as highlighted in below screen.
 ![image.png](/.attachments/image-9131576b-8fee-49de-a763-0894906df37c.png)

## 2.Deployment
### 2.1	CRM Solution Import [Automated]

The following are the CRM Customizations and related solutions shown below to be imported sequentially in the order mentioned to the required CRM online instance.

Note: The solution import should be performed by a user with System Administrator or System Customizer role.

1.	TASMU_CPM_WebResources
2.	TASMU_CPM_Core
3.	TASMU_CPM_Plugins
4.	TASMU_CPM_Processes

Please refer to Appendix A for detailed steps to import the CRM Solution.
Note: During import of managed solutions into ETE Organization, make sure to selelct ‘Overwrite Customizations option’ in ‘Import Options’ window as shown below.
 ![image.png](/.attachments/image-cced0f4a-4239-4d3c-9d4b-c0d775e8b1e3.png)

### 2.2	Additional CRM Solution Import
The following are the CRM Customizations and related solutions shown below to be imported sequentially in the order mentioned to the required CRM online instance.

Note: The solution import should be performed by a user with System Administrator or System Customizer role.

1.	TASMU_CPM_SLAs
2.	TASMU_CPM_RoutingRules

Please refer to Appendix A for detailed steps to import the CRM Solution.
Note: During import of managed solutions into ETE Organization, make sure to selelct ‘Overwrite Customizations option’ in ‘Import Options’ window as shown below.
 ![image.png](/.attachments/image-cced0f4a-4239-4d3c-9d4b-c0d775e8b1e3.png)

## 3.	Post Deployment Steps
### 3.1	Import Data [Automated]
Import the following data packages using configuration migration tool (refer Appendix B).
•	MasterData.zip

### 3.2	Updating System Settings [Automated]
1.	Sign into Dynamics 365 as System administrator user.
2.	Go to Settings and click on Administration.
3.	Go to System Settings.

### 3.2.1	General Settings
1.	Click on General Tab.
2.	Enter 60 minutes for Duration of inactivity before timeout and 10 min for inactivity warning.
![image.png](/.attachments/image-c865c73c-b7c5-4989-bb15-9bc72e4e674e.png)
 
### 3.2.2	Increase the Note attachment Limit to 20MB (20480 KB)
![image.png](/.attachments/image-3de6efc0-5cf3-4e54-a2de-7da3c57f8552.png)
 
### 3.2.3	Audit Settings
1.	Click on Auditing Tab.
2.	Select Start Auditing and Audit user access from Audit Settings.
3.	Select Common Entities, and Customer Service Entities from Enable Auditing and click on OK.
 ![image.png](/.attachments/image-a68fa140-492e-4317-860d-bc25f3c19548.png)

### 3.3	Enable Connect to Maps for Showing Work Orders in the schedule Board

1.	To enable the Map in the Schedule Board we need to Configure the Below Steps.
![image.png](/.attachments/image-a2a2d7c9-a5ce-4c8f-880d-4330cf17e5dc.png)
  
2.	If “Connected to Maps” is “Yes”, we can view the Work order in the Map view.
![image.png](/.attachments/image-90402d7d-d125-4ddb-90c2-a9614483e90e.png)

### 3.4	Configure customer voice survey on case resolve.

1.	Browse customer voice URL and create new Project.  In Project Template select **Support**.
https://customervoice.microsoft.com/
![image.png](/.attachments/image-e84b8208-422a-45cf-bdbc-f83cc8aed3b0.png)
 
2.	Click on Next -> select the target environment and click on **Select and Close** -> click on **Create**. Below is example for Tasmu Config environment.
![image.png](/.attachments/image-b633e72e-db38-4172-abb3-8c92dfd30451.png)
 
3.	Expand the customization and Click on Personalization and create Case ID Variable.
![image.png](/.attachments/image-956a8ccf-19e7-43be-9ebd-39c4c457fd37.png)
![image.png](/.attachments/image-b7a8f009-926a-462b-aa09-ccab5186c65a.png)
 
4.	Edit the Design Section and add Case ID Variable in the content.

"Hi {{First Name}},We are contacting you regarding the case {{ID}} you had with us.We appreciate your business, and we hope you had a great experience with our customer service. Please share your feedback so we can make the experience even better."

![image.png](/.attachments/image-6f644559-5c10-4094-a6b5-f675ec360577.png)
 
5.	Go to Send tab and click on Edit in Power Automate and Turn on Send Survey Flow.
![image.png](/.attachments/image-0c719ccd-b197-47e4-9572-1f71c2259bc4.png)
![image.png](/.attachments/image-6cfc9a74-53fe-4196-ab28-1ad3778af50c.png)
 
### 3.5	Enable SLA Flows after deployment

1.	Go to SLA record (Service Management --> Service Level Agreement) and open SLA Record and deactivate.
![image.png](/.attachments/image-079c03df-279d-4391-9ca5-ae273dee4334.png)
 
2.	Inside SLA open SLA Item and Click on Configure.
![image.png](/.attachments/image-7f90a8df-9591-4306-a2eb-65250332fea0.png)
 
3.	It will redirect to the MS Flows click on configure and click on back arrow then turn on flow.
![image.png](/.attachments/image-5153c0e9-d206-42f2-a26f-a140e5effa02.png)
![image.png](/.attachments/image-39a7f78b-8328-42ae-a815-cdac296f5a51.png)

4.	Go back to the SLA record and activate it.

### 3.6	Case Routing Rules

1.	Once the Case Routing rules solution is imported into the target instance, manually update the Queue in the rule items and then activate the Routing rule set.
![image.png](/.attachments/image-557c3e05-f2dc-46b9-a74c-0df6e0142b69.png)
 

### 3.7	Enable Customizable Resolve Case Dialog

1.	Go to Service Management (Change Area) -> Service Configuration Settings -> Select the Style of Resolve Case Dialog box -> Customizable Dialog.
![image.png](/.attachments/image-886c1ec4-f450-40a5-9147-cb26abeb70c9.png)

### 3.8  Move Theme Data
1. We need to make sure that [themes-data.csv](/.attachments/themes-data-359d2f81-f951-48db-96db-736a4566cd46.csv) file is imported in the target environment [Follow the Appendix C - Import record from Excel ]
3. After importing, Custom theme called "Tasmu Theme" will available in the desired environment, we need to manually publish the theme in the respective environment. 

![Publish Theme.png](/.attachments/Publish%20Theme-f0de7009-2bca-4c0c-9fe2-acb0ae52b284.png)

### 3.9  Add Security Alert Workflow Automation
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
 
### 3.10 Configure export to data lake
1. Go to https://make.powerapps.com -> select the right environment -> click on Export to data lake -> click on New link to data lake.
![image.png](/.attachments/image-fd0c30f3-6fd0-48b0-83c7-da388a5639e9.png)

2. Select the right resource group, and storage account (contact data and ai team for the storage account name) and click on next.

3. Select all entities in the next screen and finish the setup. More details below.
https://docs.microsoft.com/en-us/powerapps/maker/data-platform/export-to-data-lake#select-and-export-dataverse-table-data-to-azure-data-lake-storage-gen2.

### 3.11 Create and assign security role to Application Users
1. Create the following application users by following "Appendix D - Application User Creation".

| Name | Security Role |
|--|--|
| spn-crm-common-integration-<env> | Common - Integration |
| spn-crm-profile-management-integration-<env> | Profile Management - Integration |
| spn-crm-case-management-integration-<env> | Case Management - Integration |

More details on application users below (only FYI).
https://docs.microsoft.com/en-us/powerapps/developer/data-platform/use-single-tenant-server-server-authentication#application-user-creation

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
