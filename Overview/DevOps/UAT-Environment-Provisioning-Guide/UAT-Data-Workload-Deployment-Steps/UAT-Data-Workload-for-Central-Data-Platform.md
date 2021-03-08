# Pre requisites
1. ARM Modules must be created
1. Resource Group specific deployment files must be stitched
(Refer [README.md](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FREADME.md&_a=preview) of infra repo for details)
1. Merge all the code to master branch.
1. Wait for CI pipelines to complete for the templates to be uploaded to the artifacts storage account
1. Networking and infra resources must be deployed first
1. Specific resource group components can be deployed next
1. Solution components can be deployed on the azure resources at the end

# Deployment of Azure Infrastructure

|Pipeline|Dependencies |
|--|--|


|Resource Group|rg-cpd-data-uat-we-01|
|--|--|
|Analysis Services |aascpddatauatwe01|
|Azure Databricks  | databricks-cpd-data-uat-we-01 |
|Azure Data Factory  |adf-cpd-data-uat-we-02 (Smart City, Platform Events, Cost Management) |
|Azure Data Explorer Cluster  |adxcpddatauatwe02  |
|Load Balancer  |kucompute-adxcpddatauatwe02-elb  |
|Load Balancer  |kucompute-adxcpddatauatwe02-ilb  |
|Load Balancer  |kudatamgmt-adxcpddatauatwe02-elb|
|Load Balancer  |kudatamgmt-adxcpddatauatwe02-ilb|
|Public IP address  |adxuatdmip |
|Public IP address  |adxuatpip |
|Storage Account (ADLS)  |dlsgoldzoneuatwe01  |
|Storage Account (ADLS)  |dlslandingzoneuatwe01  |
|Storage Account (ADLS)  |dlsrawzoneuatwe01  |
|Storage Account (ADLS)  |dlsopenzoneuatwe01  |
|Storage Account (ADLS)  |dlscrmuatwe01  |
|Storage Account  |stcpddatauatwe01  |
|Storage Account  |stcpddatauatwe02  |
|SQL database  |sqldb-cpd-data-uat-we-02  |
|SQL database  |sqldb-cpd-dynamics-data-uat-we-01  |
|Synapse Workspace  |snp-cpd-data-uat-we-01   |
|Synapse Workspace SQL pool |smartcity|
|Synapse Workspace SQL pool |smartparking|
|Virtual Machine  |vmdgattstwe01|
|Virtual Machine  |vmdgattstwe02|
|Virtual Machine  |vmdgattstwe03|
|Virtual Machine  |vmdgattstwe04|

|Resource Group|rg-cpd-data-sec-uat-we-01|
|--|--|
|Key Vault |kv-cpd-data-uat-we-01|


# Deployment of Data Infrastructure in following order.
### Please pay your attention to keep the proper order of activities to avoid getting errors due to lack of secrets in KeyVault.


1. [Deployment of KeyVault](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=488)
1. Prepare [library variable group](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_library?itemType=VariableGroups) in Azure DevOps by copying one of the existing variable groups - uat.
The list of secrets to be seeded to kv-cpd-data-<env>-we-01 - Scripts\KeyVault\data-secrets.yml
Stage for uat must be added to pipeline.
1. Run the pipeline to populate key vault [Deployment of KeyVault secrets](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=966)

1. Run the pipeline [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=511)

# Environment Variables for Azure Pipelines
The following list of variables are required to be updated after a new Azure infrastructure is created prior to deploying the solution components below.


|Variable Name| Description |
|--|--|
| RawZone-Key | Primary key for raw zone storage |
| GoldZone-Key | Primary key for gold zone storage |
| GoldZone-CRM-Key |Primary key for CRM storage  |
| stcpddata01-Key | Primary key for stcpddata01 storage |
| stcpddata02-Key | Primary key for stcpddata02 storage |
| SQLServer01-Admin-Password | Admin Password |
| SQLServer01-Admin-Username | Admin Username |
| Databricks-bearerToken | Generate a new user bearer tokerm from databricks portal |
| SPN-Data-Id | Service Principle Id |
| SPN-Data-Key | Service Principle Key |
| SPN-ADO-Id | Service Principle Id |
| SPN-ADO-Key | Service Principle Key |
| rawzone | Rawzone storage account name eg. dlsrawzoneuat01 |
| goldzone | Goldzone storage account name eg. dlsgoldzoneuat01|

# Update ADX Project for new Environment
Add ADX deployment scripts in the following [project](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/data-platform?path=PlatformEvents/Mcs.PlatformEvents.ADX) similar to the existing environments implementation for:
1. Deploy
1. Functions

# Deployment of the solution components (Smart City Dashboards components)
Run the following pipelines in sequence:
1. Deploy Sectorial Data (raw) -> [Environment](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=980) 
1. Deploy Sectorial Data (raw) -> [Transport](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=984) 
1. Deploy Sectorial Data (raw) -> [Logistics](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=982) 
1. Deploy Sectorial Data (raw) -> [Sport](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=988) 
1. Deploy Sectorial Data (raw) -> [Healtcare](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=986)
 
1. Deploy Sectorial Data (gold) -> [Environment](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=981) 
1. Deploy Sectorial Data (gold) -> [Transport](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=985) 
1. Deploy Sectorial Data (gold) -> [Logistics](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=983) 
1. Deploy Sectorial Data (gold) -> [Sport](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=989) 
1. Deploy Sectorial Data (gold) -> [Healtcare](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=987) 

1. [Deploy Azure Synapse DWH](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=510)
1. [Deploy Azure Data Explorer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=932)
1. [Deploy Azure Analysis Services model](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=560)
1. [Deploy Azure Data Factory - Smart City Only](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=990)

1. Create Databricks Cluster (Placeholder)
1. [Deploy Databricks Notebooks](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=474)

# Deployment of Cost Management components
Automatic export of cost management data needs to be scheduled at subscription level. At the moment this is done manually, but it can be automated. To configure this manually, follow these steps:
1. Navigate to Subscriptions, select the relevant subscription from the list, and then select Cost analysis in the menu. At the top of the Cost analysis page, select Settings, then Exports.
2. Select Add and type a name for the export. Name must follow this naming convention: "ActualCostUsage<ENV>", where <ENV> is a 3-letter acronym identifying the environment (eg dev, tst, uat, npd, prd).
3. For the Metric, select "Actual cost (Usage and Purchases)".
4. For Export type, select "Daily export of month-to-date costs".
5. Select the start date.
6. Specify the subscription for your Azure storage account, then select a resource group or create a new one. Resource group used is "rg-cpd-data-<ENV>-we-01".
7. Select the storage account name or create a new one. Storage account used is the raw zone storage, thus "dlsrawzone<ENV>we01".
8. Specify the storage container and the directory path that you'd like the export file to go to. Container must be "costmanagement" and directory path must be "archive".
9. Review your export details and select Create.

Your new export appears in the list of exports. By default, new exports are enabled.
Initially, it can take 12-24 hours before the export runs. However, it can take up longer before data is shown in exported files.
If the exports are configured as described above, and if the Azure Data Factory is configured with the proper connection, the ADF pipeline will run the workflow every day as described in the delivery document.

The data moved by the ADF into the gold zone datalake is then referenced by a Synapse Workspace view. Currently the Synapse Workspace product is not mature enough to be fully deployed via Azure Devops. Following manual steps are needed after the automatic deployment of the Synapse resource in Azure Portal:
1. Connect to snp-cpd-data-<ENV>-we-01-ondemand.sql.azuresynapse.net with Synapse Workspace Studio or with a SQL client of your choice
2. Run queries described in /CommandControl/Mcs.Tasmu.CostMgmt.SyA/CostManagementSynapseQueries, with manual steps as described inline
3. Please note that Synapse Workspace connects to the Gold Zone datalake with Shared Access Signature, which has an expire date.

# Assign all Smart City services to Log Analytics Workspace.
1. Login with az login --tenant "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX"  where "XXX..." is tenant id
1. Run the script SmartCityLogs.ps1 (PlatformEvents/Mcs.PlatformEvents.LogAnalytics/SmartCityLogs.ps1) from data-platform repo.

# Deployment of Date and Time dimensions.
1. Connect to snp-cpd-data-uat-we-01.sql.azuresynapse.net with Azure Data Studio, SSMS, Visual Studio or any other tools you can run Stored Procedure.
1. Sign in to smartcity database.
1. Run exec dbo.uspLoadDimTime to pupulate Time dimension entity.
1. Run exec dbo.uspLoadDimDate '01/01/2020','01-01-2030' where parameters are first and last date of dimension values scope.

# Deployment of Dynamics custom views
1. Connect to Dynamics database of the current environment using SSMS
1. Run the sql script in the code repo under Dynamics/Views.sql  

# Installation of Power BI data gateway.
Because all resources are closed within VNET, Power BI as a service needs to connect data through gateway installed as high availability cluster (two nodes) on VM deployed as part of infrastructure deployment. The full installation guide of PBI data gateway is available with below URL:
[Power BI data gateway installation tutorial](https://docs.microsoft.com/en-us/data-integration/gateway/service-gateway-install)

# Deployment of Power BI Reports
Currently we are deploying all the Power BI reports in the tst environment. A new workspace named “Automation Tst - Tasmu Command & Control Center Dashboards” is created where all the reports are automatically deployed.
For the automatic deployment, “Power BI: Action” extension is used.
* Automatic:
  * Deployment of Power BI reports to tst environment.
  * Update Data sources for Azure Analysis Service pointing it to the tst.
- After Automatic Deployment, we need to change few things manually.
* Manual:
  * Update Data sources for SQL (Credentials too) , ADX and Blob storage.

-	Improvement: Make the whole process automatic by writing a PowerShell script in future.

A YAML file [cd-powerbi.yaml](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/data-platform?path=%2Fpipelines%2Fdeploy%2Fcd-powerbi.yml) is created that has all the code for automatic deployment of Power BI reports.

The pipeline [cd-powerbi](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=735&_a=summary&view=runs) is triggered manually whenever any report should be deployed to Power BI workspace.






