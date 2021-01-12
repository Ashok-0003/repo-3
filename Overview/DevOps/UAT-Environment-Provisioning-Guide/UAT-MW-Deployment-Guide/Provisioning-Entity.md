**Provisioning Entity individually**

1. Entities can be provisioned using the pipline [CDO-SPO-ProvisionEntity-Uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=807) . It makes use of the file Entities.xml as reference for provisioning. 
1. This script will provision new entity site collection, list, libraries with custom views, provision user groups, add navigation menus appropriately to all sectors, marketplace, etc. 
1. This script will not create Taxonomy at TermStore or Content Types or SiteColumns at content type hub.

Below are the input parameters for the script


  

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

**Modifying Entities.xml for provisioning**
 
![image.png](/.attachments/image-1591e5ed-9deb-422e-bd6a-c00d91a7a8fb.png)

The entities.xml follows the same definition as the **Site.xml**  except that it provisions only Entities. All email ids mentioned in the file need to be changed to appropriate email ids for that specific tenant and SharePoint group.
In order to provision a new Entity for a given Sector, an **entityassociatedsite** element node needs to be created under the **Site** node of the required sector.
 
![image.png](/.attachments/image-55fca8da-6b44-4174-b1f3-b1b2e41c689d.png)
All the list of groups that need to be provisioned for that Entity along with email ids need to be mentioned under **entitySPGroup** element.

 ![image.png](/.attachments/image-0e4e43b2-e195-48e7-bdd3-ae10fa9c03bb.png)

All the list and libraries that need to be provisioned for the Entity along with their default views and custom views need to be mentioned under the xml element node **entitySPList**
 ![image.png](/.attachments/image-515c43c8-0ad3-45ff-8a42-7592c65cebfd.png)
All the webpart that would need to be added in the home page of the entity site, need to be added under **entityPageWebpart** xml element node.
![image.png](/.attachments/image-bb13729d-b68d-40a7-a646-14e253eb0861.png)
 
As navigation for the newly created Entity needs to be updated in global site and marketplace in SharePoint, the same has to be mentioned under **globalConfigNav** and **globalNav** node sections
 ![image.png](/.attachments/image-b1428712-1e0c-4d2b-bc59-9f054eb90227.png)
As navigation needs to be created for the Sector under which Entity was created, the same must be mentioned under **QuickLaunchNav** section.
 ![image.png](/.attachments/image-98f47cde-3a99-455f-9a1a-b734e54de731.png)

As top navigation of existing sectors and current sector need to be updated to include the newly provisioned Entity, the same needs to be mentioned under **TopNav** section along with all existing sectors.
 
![image.png](/.attachments/image-be402c60-98b2-48a3-bc49-37d0b394320f.png)
As navigation for the newly created Entity needs to be updated, the same has to be mentioned under the section **entityNav**
 ![image.png](/.attachments/image-744cbd44-bcf2-4c44-a977-bc4bf5302bcb.png)

All list names that would need to be updated in the configuration list of global site for the newly provisioned sector would need to come under the section **entityAddItemConfigurationList**

 ![image.png](/.attachments/image-71cc04d7-3e60-47ae-9d72-3f5210aa5cb1.png)

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

