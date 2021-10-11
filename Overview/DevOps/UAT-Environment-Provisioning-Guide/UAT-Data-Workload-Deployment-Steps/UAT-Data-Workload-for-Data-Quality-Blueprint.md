Data Quality Blueprint

**## Introduction**
The Data Quality blue print has been implemented to present the full Data Quality flow as follows:
![image.png](/.attachments/image-67ceed67-2a17-4209-a4ac-f883c7d05e8c.png)

![image.png](/.attachments/image-c604a16c-4e97-4aea-97fe-7b5cf0ebb1fa.png)


## **Implementation in UAT.**

### Services involved.

|Service|Name  |Resource Group|
|--|--|--|
|Purview  |purv-cpd-data-uat-we-01 |rg-cpd-data-uat-we-01|
|SQL  |sql-cpd-data-uat-we-03 |rg-cpd-data-uat-we-05|
|SQL database |sqldb-cpd-data-demo-uat-we-01 |rg-cpd-data-uat-we-05|
|Databricks |databricks-cpd-data-uat-we-01 |rg-cpd-data-uat-we-01|
|Azure Data Factory|adf-cpd-data-uat-we-01 |rg-cpd-data-uat-we-01|


### Implementation steps.
1. Purview is deployed within CDP pipeline.
1. [Deploy the other infrastructure](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1684).
1. [Import Data to purviewhealth container at Landing Zone](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1683) 
**_Note_**: Please check whether **dlslandingzoneuatwe01** storage account is assignet to VNET. If so, please enable free access to the storage account and after copy operation is done, restore the network assignment.
1. Add secrets to Key Vault - 
     - purview-tenantId 
     - purview-clientId
     - purview-clientSecret
     - demoPurview-SqlUser
     - demoPurview-SqlPassword

1. [SQL Database deployment with pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1680).
1. [ADF Data pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1682)
1. Databricks scripts validation.

![image.png](/.attachments/image-c7f7a932-a2b5-4ad9-b565-2ffc1b658d67.png)

- **Settings** 
  - Cmd 6 Line 12 - the Purview instance name
  - Cmd 15 Line 1 - check the SQL server name
  - Cmd 15 Line 2 - check the SQL database name
- **SchemaAndDQConformancyCheck**

- **Load_HealthCare_KPI**





