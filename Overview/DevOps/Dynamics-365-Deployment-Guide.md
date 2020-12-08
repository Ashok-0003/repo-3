1 	Purpose
The purpose of this document is to explain the steps to deploy TASMU Dynamics 365 CE Solution.

1	Pre-Deployment
1.3 Configure Queues
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
1.4 Configure Team and assign role
The following is the team to be created. 
1.	Knowledge Article Approvers

Follow steps below to create and configure above team.
1.	Go to https://make.powerapps.com -> Select the right Environment.
2.	Click on Settings on the top right corner “gear” symbol button and then on Advanced Settings button as highlighted below.
 ![image.png](/.attachments/image-012fd760-c5c7-4484-9d9b-ae57ccd1f23d.png)

3.	Navigate to Security under System area in sitemap as highlighted in below screenshot.
![image.png](/.attachments/image-ba33bda7-5b4e-47d8-94bb-59d8d6dcd0ec.png)

4.	Click on Teams as highlighted in below screenshot.
![image.png](/.attachments/image-4c5dfbd9-57df-4956-8472-cab53f68b86e.png)
 
5.	Click on ribbon button + NEW
![image.png](/.attachments/image-1ea20d7b-7052-447f-8557-61a8eedc4274.png)
 
6.	Provide the Team Name and other details as shown below and save the record.
 ![image.png](/.attachments/image-d3e44b15-25f5-4beb-9c29-b23ddf907b51.png)
7.	Click on MANAGE ROLES ribbon button and assign security role ‘Tasmu Article Approver’  to the team and click on OK button as highlighted in below screen.
 ![image.png](/.attachments/image-9131576b-8fee-49de-a763-0894906df37c.png)
2.Deployment
1.1	CRM Solution Import [Automated]

The following are the CRM Customizations and related solutions shown below to be imported sequentially in the order mentioned to the required CRM online instance.

Note: The solution import should be performed by a user with System Administrator or System Customizer role.

1.	TASMU_CPM_WebResources
2.	TASMU_CPM_Core
3.	TASMU_CPM_Plugins
4.	TASMU_CPM_Processes

Please refer to Appendix A for detailed steps to import the CRM Solution.
Note: During import of managed solutions into ETE Organization, make sure to selelct ‘Overwrite Customizations option’ in ‘Import Options’ window as shown below.
 ![image.png](/.attachments/image-cced0f4a-4239-4d3c-9d4b-c0d775e8b1e3.png)
2.	Post Deployment Steps

2.1	Import Data [Automated]
Import the following data packages using configuration migration tool (refer Appendix B).
•	MasterData.zip

2.2	Updating System Settings [Automated]
1.	Sign into Dynamics 365 as System administrator user.
2.	Go to Settings and click on Administration.
3.	Go to System Settings.

2.2.1	General Settings
1.	Click on General Tab.
2.	Enter 60 minutes for Duration of inactivity before timeout and 10 min for inactivity warning.
![image.png](/.attachments/image-c865c73c-b7c5-4989-bb15-9bc72e4e674e.png)
 
2.2.2	Increase the Note attachment Limit to 20MB (20480 KB)
![image.png](/.attachments/image-3de6efc0-5cf3-4e54-a2de-7da3c57f8552.png)
 
2.2.3	Audit Settings
1.	Click on Auditing Tab.
2.	Select Start Auditing and Audit user access from Audit Settings.
3.	Select Common Entities, and Customer Service Entities from Enable Auditing and click on OK.
 ![image.png](/.attachments/image-a68fa140-492e-4317-860d-bc25f3c19548.png)

2.3	Enable Connect to Maps for Showing Work Orders in the schedule Board

1.	To enable the Map in the Schedule Board we need to Configure the Below Steps.
![image.png](/.attachments/image-a2a2d7c9-a5ce-4c8f-880d-4330cf17e5dc.png)
  
2.	If “Connected to Maps” is “Yes”, we can view the Work order in the Map view.
![image.png](/.attachments/image-90402d7d-d125-4ddb-90c2-a9614483e90e.png)

2.4	Configure customer voice survey on case resolve.

1.	Browse customer voice URL and create new Project.  In Project Template select Support.
![image.png](/.attachments/image-e84b8208-422a-45cf-bdbc-f83cc8aed3b0.png)
 
2.	Select the Environment and Create.
![image.png](/.attachments/image-b633e72e-db38-4172-abb3-8c92dfd30451.png)
 
3.	Expand the customization and create Case ID Variable.
![image.png](/.attachments/image-b7a8f009-926a-462b-aa09-ccab5186c65a.png)
 
4.	Edit the Design Section and the Case ID Variable in the content.
![image.png](/.attachments/image-6f644559-5c10-4094-a6b5-f675ec360577.png)
 
5.	Browse Flows  and Turn on Send Survey Flow.
![image.png](/.attachments/image-6cfc9a74-53fe-4196-ab28-1ad3778af50c.png)
 
2.5	Enable SLA Flows after deployment

1.	Go to SLA record (Service Management --> Service Level Agreement) and open SLA Record and deactivate.
![image.png](/.attachments/image-079c03df-279d-4391-9ca5-ae273dee4334.png)
 
2.	Inside SLA open SLA Item and Click on Configure.
![image.png](/.attachments/image-7f90a8df-9591-4306-a2eb-65250332fea0.png)
 
3.	It will redirect to the MS Flows click on configure and click on back arrow then turn on flow.
![image.png](/.attachments/image-5153c0e9-d206-42f2-a26f-a140e5effa02.png)
![image.png](/.attachments/image-39a7f78b-8328-42ae-a815-cdac296f5a51.png)

2.6	Case Routing Rules

1.	Once the Case Routing rules solution is imported into the target instance, manually update the Queue in the rule items and then activate the Routing rule set.
![image.png](/.attachments/image-557c3e05-f2dc-46b9-a74c-0df6e0142b69.png)
 

2.7	Enable Customizable Resolve Case Dialog

1.	Go to Service Management (Change Area) -> Service Configuration Settings -> Select the Style of Resolve Case Dialog box -> Customizable Dialog.
![image.png](/.attachments/image-886c1ec4-f450-40a5-9147-cb26abeb70c9.png)
 
Appendix A - Solution Import

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

Appendix B - Data Import using Configuration Migration Utility
Configuration Migration Utility is available as part of Dynamics 365 SDK.
1.	Run the tool by double clicking on the DataMigrationUtility.exe.
2.	Click on Import data and then click on Continue.
 ![image.png](/.attachments/image-9496b01c-0859-4b79-b40b-2595d35176cc.png)

3.	Select the following options, enter the credentials and then login. From the popup window, select the correct Dynamics instance.
 ![image.png](/.attachments/image-c6e6fa0a-1f4c-49fc-a19c-51b91f81c67f.png)

4.	Select the zip file containing the data and click on Import Data.
  ![image.png](/.attachments/image-e3025e03-14c5-42b1-b49e-733f974b6f9e.png)

5.	Verify whether the data is imported by opening the entity from advanced find.
