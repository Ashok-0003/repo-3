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

# Deployment of Data Infrastructure

# Environment Variables for Azure Pipelines
The following list of variables are required to be updated after a new Azure infrastructure is created prior to deploying the solution components below.


|Variable Name| Description |
|--|--|
| RawZone-Key |  |
| GoldZone-Key |  |
| GoldZone-CRM-Key |  |
| stcpddata01-Key |  |
| SQLServer01-Admin-Password |  |
| SQLServer01-Admin-Username |  |
| Databricks-bearerToken |  |
| iot_sharedAccessPolicyKey |  |
| evh_sharedAccessPolicyKey |  |
| SPN-Data-Id |  |
| SPN-Data-Key |  |
| SPN-ADO-Id |  |
| SPN-ADO-Key |  |


# Deployment of the solution components
Run the following pipelines in sequence:
1. [Deploy Azure SQLDB](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=501)
1. [Deploy Azure Synapse DWH](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=509)
1. [Deploy Azure Function Parking Lot Update](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=543)
1. [Deploy Azure Function Parking Simulator](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=544)
1. [Deploy Azure Stream Analytics Jobs](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=545)
1. [Deploy Azure Data Explorer](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=559)
1. [Deploy Azure Analysis Services model](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=560)
1. [Deploy Azure Data Factory](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=462)





