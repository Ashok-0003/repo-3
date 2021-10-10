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
1. [SQL Database deployment with pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1680).
1. ADF Pipeline deployment 
1. Databricks scripts adjustment
The full solution makes three scripts:
- Settings (to set up all the settings 
- 
All the scripts all pro
![image.png](/.attachments/image-c7f7a932-a2b5-4ad9-b565-2ffc1b658d67.png)
    - check whether kv-cpd-data-uat-we-01 instance is added as 




