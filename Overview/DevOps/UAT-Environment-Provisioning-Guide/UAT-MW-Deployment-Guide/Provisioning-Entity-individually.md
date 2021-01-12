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