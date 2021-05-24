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

1. Run the pipeline [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1559)

