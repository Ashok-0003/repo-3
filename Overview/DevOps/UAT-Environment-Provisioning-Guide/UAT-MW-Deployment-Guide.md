**SharePoint Online Artifacts Provisioning** 
 
1. Add SharePoint Administration account as a site collection administrators. 
2. Make sure the users Email Address are updated correctly in the “Scripts/CMS/ProvisioningScripts/resources/site.xml”
3. Please check below image for reference

![user_group_TASMU.PNG](/.attachments/user_group_TASMU-e3955649-ead0-4abc-a669-f794bb5b1eda.PNG)

The highlighted section of the above image needed to be modified with the correct users. This should be done for all the groups mentioned in the above image both for marketplace (*globalSPGroup*) and sectors (*SectorSPGroup*)
4. Trigger the pipeline [CD-SPO-Provision-Uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=593) by clicking on the link.
Once clicked , you will land on below page. 

![run_uat_pipeline_TASMU.PNG](/.attachments/run_uat_pipeline_TASMU-129db537-c02b-4c8c-bbb6-b513e0d37b8e.PNG)
If you need to edit/update any variables, click on the Edit button, or if you want to Run the pipeline, click 'Run pipeline'.

a. If you click *Edit* button, the system will take you to the Edit page of the pipeline as shown below.

![uat_pipeline_variables_TASMU.PNG](/.attachments/uat_pipeline_variables_TASMU-fc9bc749-8a1f-4207-9be3-7c050afc10be.PNG)
If you want to edit/modify any variables, click on *Variable* button

![uat_variables_modification_TASMU.PNG](/.attachments/uat_variables_modification_TASMU-32818179-5b19-4fd2-91a7-87c0558f0e3e.PNG)

b. If you click *Run Pipeline* button, system will take you to below page for the final confirmation. 

![run_from_master_branch_TASMU.PNG](/.attachments/run_from_master_branch_TASMU-7a6e57a4-1692-4978-b9eb-598aa7891a9e.PNG)

Select the branch **master** and click on the *Run* button to start the pipeline. 
The variable input details is provided below. 

.INPUTS 

  

    tenant                  - This is the name of the tenant that you are running the script 

    TemplateParametersFile  - This should be the json file having RoleName for Logging 

    sp_user                 - This is the user email ID of the tenant which will be used for running the script 

    sp_password             - This is the user password of the tenant which will be used for running the script 

    scope                   - This is the scope for Search Configuration of the tenant which will be used for running the script, example, Subscription 

    InstrumentationKey      - This is the Instrumentation Key which will be used for logging Exceptions in Azure Application Insight  

  

Example :  

param ( 

    $tenant = "M365B188241", 

    $TemplateParametersFile = "parameter.json", 

    $sp_user = "admin@M365B188241.onmicrosoft.com", 

    $sp_password = "a064Not9xH", # Note this value is a secret in the pipeline variable

    $scope = "subscription", 

    $InstrumentationKey = “984ca526-2038-4d9d-b0cf-653706512c58”  # Note this value is a secret in the pipeline variable

) 



  Keep monitoring to see if it is creating all the terms, columns, content types, lists and provisioning other features! 

**Post Deployment Steps**
- For Translation of Site Titles and Navigation Bar content

1. Change the necessary URLs for your sites in Scripts/CMS/ProvisioningScripts/resources/Arabic.xml file

     ![image.png](/.attachments/image-d50715f4-2390-4b54-a74d-0d0e69009d18.png)
 
1. Make sure the default language for cms.automation account is set to Arabic in the Office profile
     ![image.png](/.attachments/image-da51dc53-4c85-4e2d-ac44-176896a27e7f.png)
     Steps to add a new language : https://support.microsoft.com/en-us/office/change-your-personal-language-and-region-settings-caa1fccc-bcdb-42f3-9e5b-45957647ffd7
1. Go to pipeline [CD-SPO-NavTrans-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=722)
1. Update the necessary variables and run the pipeline.
     ![image.png](/.attachments/image-987edea8-bafa-4bac-91ac-1e1080cbd883.png)

- For translation of list titles, content types, field names :

 Download this zip file **Scripts/CMS/ProvisioningScripts/resources/ResourceFileTranslation.zip** to your system and extract it to a folder.
 
For each of the sites repeat the following steps
1. Go to site settings and click on Export Translations

     ![image.png](/.attachments/image-8af24e25-4685-4883-aa63-d429b65c9786.png)
1. Choose the language as Arabic and click on Export, a file will get downloaded to your system.

     ![image.png](/.attachments/image-9bf1df77-9f48-4509-b216-b5584f717b38.png)
1. Copy the downloaded resource file to the folder where the zip file is extracted.    
1. Open UdatedResx.ps file in notepad, and edit the first line of the file, update the name of your resource(.resx) file and save it.
   ![image.png](/.attachments/image-ce5232e5-0984-42a2-b60e-8f2ffeb28a2b.png)
1. Open Powershell on your system and run the following commands:

    i) `cd <Path to your extracted folder>` eg: cd C:\Users\XXXXX\Downloads\ResourceFileTranslation

   ii) `.\UpdateResx.ps1`
Once you get the message "File Updated Successfully" on the powershell, proceed to step 6. 
1. Go to site settings and click on Import Translations
     ![image.png](/.attachments/image-c35e80ae-eb45-4207-8a20-9de2cac55ca0.png)
1. Click on Browse, select the updated resx file and click on Import
     ![image.png](/.attachments/image-66e202fa-990a-4b7e-a735-993793180dd7.png)
Video Link :
- For translation of site pages:
1. Go to site settings and click on Language Settings.
![image.png](/.attachments/image-dd61eafd-6f90-465c-9491-18ac86119305.png)
2. Enable this option, add Arabic language, click on save.
![image.png](/.attachments/image-01c0fd34-543c-4f3d-962b-ac7f9176a2a5.png)
3. Go to the page and click on Translation.
![image.png](/.attachments/image-8e0f24fd-2e11-4b24-bdee-f27677ee4db0.png)
4. A panel will open up at right side of the window, click on create.
![image.png](/.attachments/image-18070354-8942-49cb-b428-ef0e7de78b03.png)
5. Click on view.
![image.png](/.attachments/image-b2262867-9ae7-4e7c-a439-3bdb7dae3215.png)
6. A new page will open up with url ending with `SitePages/ar/<PageName>.aspx`. Click on edit.
![image.png](/.attachments/image-e99848e5-e9c5-44f6-8730-32e085b5ea43.png)
7. Once the page is in edit mode, for each of the webpart, click on the webpart and update only the **title property** of the webpart to Arabic(eg: News Articles is the title of the selected webpart).
![image.png](/.attachments/image-7b99ad7f-17cd-44fb-b4f0-87871b9bb5f6.png)
8. Once all the webparts title are updated, click on Publish button. 
![image.png](/.attachments/image-f3c0b594-6e51-490f-9822-e8be823e6b27.png)

   Video Link :

- Steps to Update office 365 tenant theme and logo : [Update o365 Tenant](https://docs.microsoft.com/en-us/microsoft-365/admin/setup/customize-your-organization-theme?view=o365-worldwide)
Video Link :

- Steps to enable office 365 usage analytics permissions : [Enable Analytics permission](https://docs.microsoft.com/en-us/microsoft-365/admin/usage-analytics/enable-usage-analytics?view=o365-worldwide)
Video Link :