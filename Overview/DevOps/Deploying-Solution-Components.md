# Pre requisites
1. ARM Modules must be created
1. Resource Group specific deployment files must be stitched
(Refer [README.md](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FREADME.md&_a=preview) of infra repo for details)
1. Merge all the code to master branch.
1. Wait for CI pipelines to complete for the templates to be uploaded to the artifacts storage account
1. Networking resources must be deployed first
1. Global shared resources next
1. Specific resource group components can be deployed next
1. Solution components can be deployed on the azure resources at the end

# Deployment of Azure Infrastructure
CD-<ResourceGroupName>-Master-Release


| Pipeline Name | Estimated First run  | Incremental Run|
|--|--|--|
|[CD-rg-cpd-glob-npd-we-01-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=33)|||
|[CD-rg-cpd-pltf-net-dev-we-01-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=79)| 5 mins| 2 mins
|[CD-rg-cpd-apps-dev-we-01-Master-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=181)| 60 mins  | 5 mins|

APIM Internal VNet deployment takes 40 - 60 mins

# Deployment of the solution components
CD-<RepoName>-Release

|Step| per API |overall  |
|--|--|--|
| Build docker images |  2 mins|  35 mins|

1. Seed app configurations and key vault references - 20s
1. Deploy all APIs using helm charts - 2 mins



1. [CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build/results?buildId=5014)
Build - 35 mins
Dev - 3 min
Test - 3 min
1. [CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)
Build - 10 mins
Dev - 1 min
Test - 1 min
1. [CD-Integration-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=301)
Build - 40s
Dev - 1 min
Test - 1 min


