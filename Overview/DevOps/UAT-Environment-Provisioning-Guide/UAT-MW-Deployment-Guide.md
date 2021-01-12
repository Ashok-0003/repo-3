**SharePoint Online Artifacts Provisioning** 
 
1. Add SharePoint Administration account as a site collection administrators. 
2. Make sure the users Email id is right in the “resources\site.xml” 
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

5. Provide the below inputs as provided in the example.

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

    $sp_password = "a064Not9xH", 

    $scope = "subscription", 

    $InstrumentationKey = “984ca526-2038-4d9d-b0cf-653706512c58” 

) 



  Keep monitoring to see if it is creating all the terms, columns, content types, lists and provisioning other features! 

**Post Deployment Steps**
- For Translation of Site Titles and Navigation Bar content

1. Change the necessary URLs for your sites in Scripts/CMS/ProvisioningScripts/resources/Arabic.xml file

     ![image.png](/.attachments/image-276c9b6b-3ed0-45c8-a0f3-4625d6f389c8.png)
 
1. Make sure the default language for cms.automation account is set to Arabic in the Office profile
     ![image.png](/.attachments/image-279f71f9-36c4-4398-b6cf-c029211ca25c.png)
     Steps to add a new language : https://support.microsoft.com/en-us/office/change-your-personal-language-and-region-settings-caa1fccc-bcdb-42f3-9e5b-45957647ffd7
1. Go to pipeline [CD-SPO-NavTrans-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=722)
1. Update the necessary variables and run the pipeline.
     ![image.png](/.attachments/image-be71b248-fefe-4f1a-9b1e-03c3b8dd5de1.png)

- For exporting and importing resource files 
For each of the sites repeat the following steps
1. Go to site settings and click on Export Translations

     ![image.png](/.attachments/image-06550a0c-cc25-4219-bfaa-d9dd2201c348.png)
1. Choose the language as Arabic and click on Export, a file will get downloaded to your system.

     ![image.png](/.attachments/image-ddfbc8aa-c72b-4ab8-a6a0-77f3996c5cc0.png)
1. Download the CSV Scripts/CMS/ProvisioningScripts/resources/Translations.csv in your system.   
1. Copy the script Scripts/CMS/ProvisioningScripts/UpdateResx.ps1, make the necessary changes and run it in your system 
     ![image.png](/.attachments/image-5c816892-15ab-41fb-8fdb-7a668c00a7a5.png)
1. Go to site settings and click on Import Translations
     ![image.png](/.attachments/image-06550a0c-cc25-4219-bfaa-d9dd2201c348.png)
1. Click on Browse, select the updated resx file and click on Import
     ![image.png](/.attachments/image-548a8d21-538d-4b3d-aac9-9d65e5ece340.png)


