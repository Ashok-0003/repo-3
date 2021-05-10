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

## All the services deployed for UAT Central Data Platform.
|Resource Group|rg-cpd-data-uat-we-03|
|--|--|
|Azure SQL Managed Instance |sqlmi-cpd-data-uat-01|
|Virtual Machine with SQL database  |vmcpddatauatwe05|

## Deployment of Data Infrastructure in following order.
### Please pay your attention to keep the proper order of activities to avoid getting errors due to lack of secrets in KeyVault.

1. Run the pipeline [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=511)

# Deployment of UAT Blueprint 3
## Environment Variables for Azure Pipelines
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


**Files in Landingzone**
1. All the sectorial data files must be uploaded to the KPI folder of the container of respective sector.

For example:
- healthcare/KPI
- sport/KPI

![image.png](/.attachments/image-55dd72a1-bf22-4846-b1a1-946441aa7659.png)

2. A particular naming convention has to be followed for all the files. It should start with sector abbreviation and end with a date.
For example: 
- HLT_005_Perc pop with hlt file access prov_2020-10-29.csv
- SPR_001_Number of Gym memberships_2020-12-03.csv

3. [Run the sectorial data pipeline.](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1539)

**Run the following pipelines in sequence:**

1. Make sure that DevOps SPN has Storage BLOB Contributor role for gold and raw zone storages.
