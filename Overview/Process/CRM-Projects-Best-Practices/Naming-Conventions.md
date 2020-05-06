CRM Publisher Name -
TASMU Smart Qatar Central Platform Publisher
CRM Solution Name 
TASMU_CPM_Core
CRM Customization Prefix
CPM_
API- Project Namespace ?
TASMU.Core.[Profile].API

Publisher:
Customer Name : TASMU
Publisher Name : TASMU Smart Qatar Central Platform Publisher
Customer Solution Prefix : CPM_

Solution Names
Format : [CustomerName]_[CustomerSolutionPrefix]_[Solution]
Example : TASMU_CPM_Core; TASMU_CPM_SerurityRoles; TASMU_CPM_WebResources etc.  
Lookup Fields – the only field that should have id at the end of it simulating the PGs
Best Practices:  [CustomerSolutionPrefix_][entityname]id
Example :
Account would be CPM_accountid
Contact would be CPM_contactid
 Organization Data – if the data is global/static lookup lists
Disable recently used on the control on the form.
Make these Organization Level security.  If user or team, please give justification for why. 
Turn off all features, including Activities, Connections, Mail Merge, etc. 
Format:  [CustomerSolutionPrefix_]lookup_intakestatus
Example :
Intake Status would be CPM _lookup_intakestatus
Plugins
Format : [CustomerSolutionPrefix].Plugins.[EntityName]
Example : CPM.Plugins.Intake

 
Plugin Steps/Classes
Format : [CustomerSolutionPrefix].Plugins.[EntityName].[Process]
Example : CPM.Plugins.Intake.IntakeProcessing

 
Web Resources – JavaScript
Format : [CustomerSolutionPrefix_]/scripts/[scriptname].js
Example : CPM_/scripts/IntakeFunctions.js

 
Web Resources – HTML
Format : [CustomerSolutionPrefix_]/html/[scriptname].html
Example : CPM_/html/Welcome.html

 
Web Resources – PNG
Format : [CustomerSolutionPrefix_]/images/[imagename].png
Example : CPM_/images/intakeicon32.png (16X16 would be 16)

 
Web Resources – SVG
Format : [CustomerSolutionPrefix_]/images/[imagename].svg
Example : CPM_/images/intakeicon.svg

 
Processes – Workflows
Best Practice:  [EntityName] – [Process Name]
Example : CPM :  Intake – Assign to Risk Assessment Team
Guidance:
For Workflows that have “SEND EMAIL” step should NOT be combined within a Workflow.  These should be separate and ASYNC or via Power Automate.  This is because email failures shouldn’t stop the process.
Email workflows should begin with Notification – [Process Name], so they can be easily searched and deactivated for troubleshooting.  

 
Business Rules
Format : [EntityName] – [Process Name]
Example : CPM :  Intake – Set Required Fields on Type Change
