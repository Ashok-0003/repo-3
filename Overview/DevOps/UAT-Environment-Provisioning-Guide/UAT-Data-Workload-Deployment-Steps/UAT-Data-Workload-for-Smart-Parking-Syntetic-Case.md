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


|Resource Group|rg-cpd-data-uat-we-02|
|--|--|
|API Connection |apicon-cpd-data-eh-uat-we-01 (apicon-cpd-data-eh-uat-we-01-parameters.json) |
|API Connection  |apicon-cpd-data-sql-uat-we-01 (apicon-cpd-data-sql-uat-we-01-parameters.json)  |
|Function App  |func-cpd-data-uat-we-01  |
|Function App  |func-cpd-data-uat-we-02  |
|Function App  | func-cpd-telsim-uat-we-01 |
|App Service Plan  | plan-cpd-data-uat-we-01 |
|Application Insight  | appi-cpd-data-uat-we-01 |
|Azure Data Explorer Cluster  |adxcpddatauatwe02  |
|Azure Data Factory  |adf-cpd-data-uat-we-02 (Smart Parking) |
|Event Hubs Namespace   |evh-cpd-data-uat-we-01ns  |
|Event Hubs Namespace   |evh-cpd-data-uat-we-02ns  |
|Azure IoT Hub  |iot-cpd-data-uat-we-01  |
|Load Balancer  |kucompute-adxcpddatauatwe02-elb  |
|Load Balancer  |kucompute-adxcpddatauatwe02-ilb  |
|Load Balancer  |kudatamgmt-adxcpddatauatwe02-elb|
|Load Balancer  |kudatamgmt-adxcpddatauatwe02-ilb|
|Log Analytics Workspace  |iot-cpd-data-uat-we-02  |
|Logic App  |logic-cpd-data-uat-we-01  |
|Public IP address  |adxuatdmip02 |
|Public IP address  |adxuatpip02 |
|SQL database  |sqldb-cpd-data-uat-we-01  |
|SQL database  |sqldb-cpd-dynamics-data-uat-we-01  |
|SQL server  |sql-cpd-data-uat-we-01  |
|Storage Account  |stcpddatauatwe03  |
|Storage Account  |stcpddatauatwe04  |
|Stream Analytics job  |asa-cpd-data-uat-we-01  |
|Stream Analytics job  |asa-cpd-data-uat-we-02  |
|Stream Analytics cluster  |asa-cpd-data-uat-we-03  |

|Resource Group|rg-cpd-data-sec-uat-we-02|
|--|--|
|Key Vault |kv-cpd-data-uat-we-01|


# Deployment of Data Infrastructure in following sentence.

### Please pay your attention to keep the proper order of activities to avoid getting errors due to lack of secrets in KeyVault.




1.  Run the pipeline [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1692)

# Environment Variables for Azure Pipelines
The following list of variables are required to be updated after a new Azure infrastructure is created prior to deploying the solution components below.


|Variable Name| Description |
|--|--|
| stcpddata03-Key | Primary key for stcpddatauat03 storage |
| SQLServer02-Admin-Password | Admin Password |
| SQLServer02-Admin-Username | Admin Username |
| iot_sharedAccessPolicyKey | IOT policy key |
| evh_sharedAccessPolicyKey | Event Hub policy key |



# Update ADX SmartParking Project for new Environment (check)
Add ADX deployment scripts in the following [project](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/data-platform?path=%2FSmartParking%2FMcs.Tasmu.SmartParking.ADX) similar to the existing environments implementation for:
1. Deploy
1. Functions
1. Policies 
1. Tables
# Check availability of services
Before you start, please check in rg-cpd-data-uat-we-01 resource group if:
- Data Lake raw zone (**spsimulator** container)
- Synapse SmartParking SQL pool
- Databricks (**add notebook here**)

services has been deployed and running.

# Deployment of the solution components (Synthetic Use Case components (not production ready!))
Run the following pipelines in sequence:
1. [Deploy Azure SQLDB](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=501)
1. [Deploy Azure Function Parking Lot Update](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=543)
1. [Deploy Azure Function Parking Simulator](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=544)
1. [Deploy Azure Function Telemetry Simulator](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=625)
1. [Deploy Azure Stream Analytics Jobs](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=545)
1. [Deploy Azure Data Explorer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=559)
1. [Deploy Azure Data Factory](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=462)
1. [Deploy Event Grid for Device Avaiability](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1696)

#Assign all Smart Parking services to Log Analytics Workspace.
Login with az login --tenant "XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX" where "XXX..." is tenant id
Run the script SmartParkingLogs.ps1 (PlatformEvents/Mcs.PlatformEvents.LogAnalytics/SmartParkingLogs.ps1) from data-platform repo.

# Deployment of Power BI Reports
Currently we are deploying all the Power BI reports in the TST environment. A new workspace named “Automation Tst - Tasmu Command & Control Center Dashboards” is created where all the reports are automatically deployed.
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






