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

1. Provide the below inputs as provided in the example.

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


1. Make sure you have the entries of your sites in Scripts/CMS/ProvisioningScripts/resources/Arabic.xml file

     ![image.png](/.attachments/image-1a289f4e-9d2a-4b58-a979-157a6ccaa69c.png)
 
1. Make sure the o365 default language for cms.automation account is set to Arabic
     ![image.png](/.attachments/image-279f71f9-36c4-4398-b6cf-c029211ca25c.png)
1. Make the needed changes in "resources\site.xml"
1. Trigger the [CD-SPO-Provision-Uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=593)
1. Provide the below inputs as provided in the example.

<p>
<br/><br/><br/>
</p>

  **Provisioning Sectors Individually** 

1. Individual sectors can be provisioned through the pipeline [CDO-SPO-ProvisionSector-Uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=808) . 
1. This script will make use of the file Sectors.xml to provision the sectors. 
1. This script will provision new sector site collection, list, libraries with custom views, provision user groups, add navigation menus appropriately to the new sectors and existing sectors,marketplace,etc. 
1. This script will not create Taxonomy at TermStore or Content Types and SiteColumns at content type hub.

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


<P  class=MsoNormal><B><SPAN  lang=EN-US>SectorsScript.ps1</SPAN></B><SPAN 
> will in turn call other scripts whose details are mentioned below.</SPAN></P>


<TABLE  class=MsoTableGrid  border=1  cellspacing=0  cellpadding=0 style="border-collapse:collapse;border:none">
 <THEAD>
  <TR>
   <TD  width=208  valign=top style="width:156.15pt;border:solid windowtext 1.0pt;background:#008AC8;padding:0cm 5.4pt 0cm 5.4pt">
   <P  class=MsoNormal><B><SPAN  lang=EN-US style="color:white">Script
   Name</SPAN></B></P>
   </TD>
   <TD  width=221  valign=top style="width:165.55pt;border:solid windowtext 1.0pt;border-left:none;background:#008AC8;padding:0cm 5.4pt 0cm 5.4pt">
   <P  class=MsoNormal><B><SPAN  lang=EN-US style="color:white">Description</SPAN></B></P>
   </TD>
   <TD  width=194  valign=top style="width:145.8pt;border:solid windowtext 1.0pt;border-left:none;background:#008AC8;padding:0cm 5.4pt 0cm 5.4pt">
   <P  class=MsoNormal><B><SPAN  lang=EN-US style="color:white">Supporting
   Xml for Input</SPAN></B></P>
   </TD>
  </TR>
 </THEAD>
 <TR>
  <TD  width=208  valign=top style="width:156.15pt;border:solid windowtext 1.0pt;border-top:none;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN>SectorScript.ps1</SPAN><SPAN  lang=EN-US></SPAN></P>
  </TD>
  <TD  width=221  valign=top style="width:165.55pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>Main
  script used to provision sectors</SPAN></P>
  </TD>
  <TD  width=194  valign=top style="width:145.8pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>Sectors.xml</SPAN></P>
  </TD>
 </TR>
 <TR>
  <TD  width=208  valign=top style="width:156.15pt;border:solid windowtext 1.0pt;border-top:none;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN style="color:black">createnewsectorsitescript.ps1</SPAN><SPAN></SPAN></P>
  <P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN 
  lang=EN-US>&nbsp;</SPAN></P>
  </TD>
  <TD  width=221  valign=top style="width:165.55pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>Used
  to create new sector sitecollections</SPAN></P>
  </TD>
  <TD  width=194  valign=top style="width:145.8pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>Sectors.xml</SPAN></P>
  </TD>
 </TR>
 <TR>
  <TD  width=208  valign=top style="width:156.15pt;border:solid windowtext 1.0pt;border-top:none;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN style="color:black">provisionnewsectorsitecollectionscript.ps1</SPAN><SPAN></SPAN></P>
  <P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN>&nbsp;</SPAN></P>
  </TD>
  <TD  width=221  valign=top style="width:165.55pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>This
  contains the core logic of the sector provisioning to create list,
  libraries,groups,views,etc</SPAN></P>
  </TD>
  <TD  width=194  valign=top style="width:145.8pt;border-top:none;border-left:
  none;border-bottom:solid windowtext 1.0pt;border-right:solid windowtext 1.0pt;padding:0cm 5.4pt 0cm 5.4pt">
  <P  class=MsoNormal><SPAN  lang=EN-US>Sectors.xml</SPAN></P>
  </TD>
 </TR>
</TABLE>

<P  class=MsoNormal><SPAN  lang=EN-US style="font-size:10.0pt;line-height:115%">&nbsp;</SPAN></P>

**Modifying Sectors.xml for provisioning**

![image.png](/.attachments/image-6b3a72e6-aeb3-433a-8b20-3b66e4a15ae6.png)
<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
  
  
  
  
  
  
  
  
  
  
  
  
 
 
 

 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>The sectors.xml follows the same definition
as the <B>Site.xml</B> except that it provisions only sectors
. All email ids mentioned in the file needs to be changed to appropriate
email ids for that specific tenant and SharePoint group.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>In order to provision a new sector a <B>Site</B>
element node for the same need to be created</SPAN></P>

![image.png](/.attachments/image-0275ab9b-8540-46c5-911e-0c559d40e6ee.png)

<P  class=MsoNormal><SPAN  lang=EN-US>

</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the list of groups that need to be provisioned
for that sector along with email ids need to be mentioned under <B>sectorSPGroup
</B>element.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 ![image.png](/.attachments/image-a821b7c7-1e40-43e7-bf66-1737fc0cad59.png)
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the list and libraries that need to be provisioned
for the sector along with their default views and custom views need to be mentioned
under the xml element node <B>sectorSPList</B></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 ![image.png](/.attachments/image-988fba08-ede3-4ac6-9bc1-e93e9204c480.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the webpart that would need to be added
in the home page of the sector site, need to be added under <B>sectorPageWebpart</B>
xml element node.</SPAN>
</P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
![image.png](/.attachments/image-d598d210-6c67-4c1a-8ab3-dbb79301eb2f.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>
<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As navigation for the newly created sector needs
to be updated in global site and marketplace, the same has to be mentioned under
<B>glbalConfigNav</B> and <B>globalNav</B></SPAN></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
![image.png](/.attachments/image-0905f180-9029-4523-8bd4-0ce4876b4e18.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As navigation needs to be created for the sector,
the same has to be mentioned under <B>QuickLaunchNav</B> section.</SPAN></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
![image.png](/.attachments/image-72a8b225-8db5-45f3-96de-7adf99d17cec.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>

<P  class=MsoNormal><B><SPAN  lang=EN-US>&nbsp;</SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As top navigation of existing sectors and current
sector need to be updated to include the newly provisioned sector, the same needs
to be mentioned under <B>TopNav</B> section along with all existing sectors.</SPAN></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
![image.png](/.attachments/image-9f09c8f9-c16e-4753-b647-c05ec6d1058f.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>
<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN 
lang=EN-US style="color:black">All list names that would
need to be updated in the configuration list of global site for the newly provisioned
sector would need to come under the section </SPAN><B><SPAN style="color:black">sectorAddItemConfigurationList</SPAN></B></P>

<P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><B><SPAN style="color:black">&nbsp;</SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P> 

<P  class=MsoNormal><SPAN  lang=EN-US>
 
![image.png](/.attachments/image-93c8c7d8-8b98-49c5-8418-b91b674118ef.png)
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>

<p>
<br/><br/><br/>
</p>

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
