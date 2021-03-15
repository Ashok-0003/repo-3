# Pre requisites
1. ARM Modules must be created
1. Resource Group specific deployment files must be stitched
1. Merge all the code to master branch.
1. Wait for CI pipelines to complete for the templates to be uploaded to the artifacts storage account
1. Specific resource group components can be deployed next
1. ML Studio files will be deployed manually.

# Deployment of Azure Infrastructure

|Pipeline|Dependencies |
|--|--|


|Resource Group|rg-cpd-data-uat-we-04|
|--|--|
|Application Insight |appcpddatauatwe04|
|Key Vault  | kv-cpd-data-uat-we-02 |
|Machine Learning Workspace  |mlcpddatauatwe01 |
|Storage Account  |sacpddatauatwe05 |

![image.png](/.attachments/image-3a29679a-463d-4b3e-aaf1-ad140a211dd4.png)

# Deployment of Data Infrastructure in following order.
### Please pay your attention to keep the proper order of activities to avoid getting errors due to lack of secrets in KeyVault.



1. Run the pipeline [Deployment of master infra pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1187)
1. Manually deploy files available in REPO (MLSample folder in data-platform repository)
- [ ] Download subfolder of MLSample folder in repo  into local host.
- [ ] Open the ML workspace and select Notebooks in menu (on red) .
- [ ] Select username folder and extend sub-menu (...)
- [ ] Select Upload folder option (on green)
![image.png](/.attachments/image-833b4297-7443-481f-a7be-0a75df0ebcd2.png)
- [ ] Choose the local folder you downloaded before.
![image.png](/.attachments/image-97d4ab74-45c3-46e3-b3a3-7b7d6c5037d1.png)
- [ ] Confirm and upload the data.

ML workspace is ready to work with sample data.
