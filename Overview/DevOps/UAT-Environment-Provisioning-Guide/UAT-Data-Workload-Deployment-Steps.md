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
|API Connection |apicon-cpd-data-uat-we-01  |
|API Connection  |apicon-cpd-data-uat-we-02  |
|Function App  |func-cpd-data-uat-we-01  |
|Function App  |func-cpd-data-uat-we-02  |
|Function App | func-cpd-data-uat-we-03 |
|Function App  | func-cpd-telsim-uat-we-01 |
|App Service Plan  | plan-cpd-data-uat-we-01 |
|Application Insight  | appi-cpd-data-uat-we-01 |
|Azure Databricks  | databricks-cpd-data-uat-we-01 |
|Azure Data Factory  |adf-cpd-data-uat-we-01  |
|Azure Data Explorer Cluster  |adxcpddatauatwe01  |
|Event Hubs Namespace   |evh-cpd-data-uat-we-01ns  |
|Event Hubs Namespace   |evh-cpd-data-uat-we-02ns  |
|Azure IoT Hub  |iot-cpd-data-uat-we-01  |
|Load Balancer  |kucompute-adxcpddatauatwe01-elb  |
|Load Balancer  |kucompute-adxcpddatauatwe01-ilb  |
|Load Balancer  |kudatamgmt-adxcpddatauatwe01-elb|
|Load Balancer  |kudatamgmt-adxcpddatauatwe01-ilb|
|Log Analytics Workspace  |iot-cpd-data-uat-we-01  |
|Logic App  |logic-cpd-data-uat-we-01  |
|Public IP address  |adxuatdmip |
|Public IP address  |adxuatpip |
|SQL database  |sql-cpd-data-uat-we-01  |
|SQL database  |sql-cpd-dynamics-data-uat-we-01  |
|Dedicated SQL pool  |sqldw-cpd-data-uat-we-01  |
|Dedicated SQL pool  |sqldw-smartcity-data-uat-we-01  |
|SQL server  |sql-cpd-data-uat-we-01  |
|Storage Account (ADLS)  |dlsgoldzoneuatwe01  |
|Storage Account (ADLS)  |dlslandingzoneuatwe01  |
|Storage Account (ADLS)  |dlsrawzoneuatwe01  |
|Storage Account (ADLS)  |dlsopenzoneuatwe01  |
|Storage Account (ADLS)  |dlscrmuatwe01  |
|Storage Account  |stcpddatauatwe01  |
|Storage Account  |stcpddatauatwe02  |
|Stream Analytics job  |asa-cpd-data-uat-we-01  |
|Stream Analytics job  |asa-cpd-data-uat-we-02  |
|Synapse Workspace  |snp-cpd-data-uat-we-01   |
|Virtual Machine  |vmdgattstwe01|
|Virtual Machine  |vmdgattstwe02|
|Virtual Machine  |vmdgattstwe03|
|Virtual Machine  |vmdgattstwe04|

|Resource Group|rg-cpd-data-sec-uat-we-01|
|--|--|
|Key Vault |kv-cpd-data-uat-we-01|


# Deployment of Data Infrastructure
1. [Deployment of KeyVault](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=488)
1. [Deployment of KeyVault secrets](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=493)
1. [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=511)

# Environment Variables for Azure Pipelines
The following list of variables are required to be updated after a new Azure infrastructure is created prior to deploying the solution components below.


|Variable Name| Description |
|--|--|
| RawZone-Key | Primary key for raw zone storage |
| GoldZone-Key | Primary key for gold zone storage |
| GoldZone-CRM-Key |Primary key for CRM storage  |
| stcpddata01-Key | Primary key for stcpddata01 storage |
| SQLServer01-Admin-Password | Admin Password |
| SQLServer01-Admin-Username | Admin Username |
| Databricks-bearerToken | Generate a new user bearer tokerm from databricks portal |
| iot_sharedAccessPolicyKey | IOT policy key |
| evh_sharedAccessPolicyKey | Event Hub policy key |
| SPN-Data-Id | Service Principle Id |
| SPN-Data-Key | Service Principle Key |
| SPN-ADO-Id | Service Principle Id |
| SPN-ADO-Key | Service Principle Key |

# Update ADX Project for new Environment
Add ADX deployment scripts in the following [project](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/data-platform?path=%2FSmartParking%2FMcs.Tasmu.SmartParking.ADX) similar to the existing environments implementation for:
1. Deploy
1. Functions
1. Policies 
1. Tables

# Deployment of the solution components (Synthetic Use Case components (not production ready!))
Run the following pipelines in sequence:
1. [Deploy Azure SQLDB](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=501)
1. [Deploy Azure Synapse DWH](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=509)
1. [Deploy Azure Function Parking Lot Update](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=543)
1. [Deploy Azure Function Parking Simulator](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=544)
1. [Deploy Azure Function Telemetry Simulator](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=625)
1. [Deploy Azure Stream Analytics Jobs](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=545)
1. [Deploy Azure Data Explorer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=559)
1. [Deploy Azure Analysis Services model](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=560)
1. [Deploy Azure Data Factory](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=462)

# Deployment of the solution components (Smart City Dashboards components)
Run the following pipelines in sequence:
1. [Deploy Azure Synapse DWH](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=510)
1. [Deploy Databricks Notebooks](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=474)

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






