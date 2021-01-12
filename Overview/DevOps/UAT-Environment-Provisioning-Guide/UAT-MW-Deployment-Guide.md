**SharePoint Online Artifacts Provisioning** 
 
1. Add SharePoint Administration account as a site collection administrators. 
1. Make sure the users Email id is right in the “resources\site.xml” 
1. Make the needed changes in "resources\site.xml"
1. Trigger the [CD-SPO-Provision-Uat-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=593)
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

![image.png](/.attachments/image-56fbca91-676b-4f9a-9d75-663084b212fd.png)
<P  class=MsoNormal><SPAN  lang=EN-US>

</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the list of groups that need to be provisioned
for that sector along with email ids need to be mentioned under <B>sectorSPGroup
</B>element.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the list and libraries that need to be provisioned
for the sector along with their default views and custom views need to be mentioned
under the xml element node <B>sectorSPList</B></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>All the webpart that would need to be added
in the home page of the sector site, need to be added under <B>sectorPageWebpart</B>
xml element node.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>&nbsp;</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As navigation for the newly created sector needs
to be updated in global site and marketplace, the same has to be mentioned under
<B>glbalConfigNav</B> and <B>globalNav</B></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As navigation needs to be created for the sector,
the same has to be mentioned under <B>QuickLaunchNav</B> section.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P>

<P  class=MsoNormal><B><SPAN  lang=EN-US>&nbsp;</SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>As top navigation of existing sectors and current
sector need to be updated to include the newly provisioned sector, the same needs
to be mentioned under <B>TopNav</B> section along with all existing sectors.</SPAN></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><SPAN  lang=EN-US></SPAN></P>

<P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><SPAN 
lang=EN-US style="color:black">All list names that would
need to be updated in the configuration list of global site for the newly provisioned
sector would need to come under the section </SPAN><B><SPAN style="color:black">sectorAddItemConfigurationList</SPAN></B></P>

<P  class=MsoNormal style="margin:0cm;line-height:14.25pt;background:white"><B><SPAN style="color:black">&nbsp;</SPAN></B></P>

<P  class=MsoNormal><SPAN  lang=EN-US>
 
 
 
 
 
</SPAN><B><SPAN  lang=EN-US></SPAN></B></P> 

