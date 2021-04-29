Content in this section is subject to change as new features are released!
It for now reflects what has been presented in the blueprint demo on 15th April 2021.

# Data Flow :
![image.png](/.attachments/image-2cdf3089-d810-4069-876c-cd190d51ecfa.png)

# Resources : 
## Azure Synapse workspace: 
- Name : snp-cpd-data-dev-we-02

## Azure Data Lake Storage
- Name : dlscprawdatadevwe02

# Models Artifacts
## Source Model

[ServiceProviderSM.json](/.attachments/ServiceProviderSM-2bdaa2b7-3431-4c35-b36d-f8e4bc05811a.json)

`#Create Basemodel from sample files`

az datamodel basemodel version create
    --name MyBasemodel
    --version 0.0.1
    --basemodel-description "description of basemodel"
    --version-description "description of basemodel version"
    --storage-account-name "myAdlsAccount"
    --container-name "myAdlsStorage"
    --folder-path folder1/folder2
    --manifest-name core.manifest.cdm.json
    -g MyResourceGroup
    --synapse-workspace MySynapseWorkspace
    --source-type SampleData
    --data-account-name <sample-data-account-name>
    --data-access-key <sample-data-access-key>
    --data-container-name <sample-data-container>
    --data-folder-name <sample-data-folder
    --date-formats 'MM/dd/yyyy,MM-dd-yyyy' --datetime-formats 'yyyy/MM/dd hh:mm:ss,yyyy-MM-dd hh:mm:ss'`

`#Export Logical Base model`
az datamodel basemodel version export -n myBaseModel
                                      --version 0.0.1
                                      --storage-account-name mystorageaccount
                                      --container-name mycontainer
                                      --folder-path folder1/folder2

`#Export Physical Base model`
az datamodel basemodel version export -n myBaseModel
                                      --version 0.0.1
                                      --storage-account-name mystorageaccount
                                      --container-name mycontainer
                                      --folder-path folder1/folder2
                                      --type Physical

## Standard Model

[ServiceProviderSTD.json](/.attachments/ServiceProviderSTD-77c550af-1de8-4702-a3ad-c01387b6f722.json)
[MappingTemplate.xlsx](/.attachments/MappingTemplate-ed547eb0-6d67-4aff-8b59-4e38e31cd67d.xlsx)
[ServiceProviderMapping.xlsx](/.attachments/ServiceProviderMapping-0c7d1275-8e57-4abe-a09f-9049fe4cd091.xlsx)
[mapping.json](/.attachments/mapping-88101908-854c-4d84-b0de-61bdcaf1765e.json)

`#Generate the mapping.json from Excel`
az datamodel mapping generate-mapping
    --storage-account-name "MyStorageAccount"
    --container-name "excelMapping"
    --input-file "c:\idw\mapping.xslx"
    --source-model MySourceModel
    --source-model-type BaseModel
    --source-model-version 0.1.0
    --target-model MyTargetModel
    --output-file-name "C:\idw\modelmapping.json"

`#Delete if already exist`
az datamodel mapping delete -n ServiceProviderMapping -g 'rg-cpd-data-dev-we-02'

`#Create the mapping model from json`
az datamodel mapping create
    -n ServiceProviderMapping
    --mapping-directives mapping.json
    --synapse-workspace 'snp-cpd-data-dev-we-02'
    -g 'rg-cpd-data-dev-we-02'

`#Generate Source to Standard Pipelines`
az datamodel generate-pipeline
    --source-model ServiceProviderSM
    --target-model ServiceProviderSTD
    --model-mapping ServiceProviderMapping
    --source-data-linked-service AzureDataLakeStorage
    --source-data-container source --source-data-folder data
    --source-corpus-folder logical --type AdlsToAdls
    --target-data-linked-service AzureDataLakeStorage
    --target-data-container standard
    --target-data-folder data
    --target-corpus-folder logical
    -g 'rg-cpd-data-dev-we-02'
    --generate-partial-pipeline
    --overwrite-synapse-resource


## Analytical and Reports
[ServiceProviderAM.json](/.attachments/ServiceProviderAM-33281371-5ba6-422b-bb2f-e608f3be79e0.json)

`#Create the Analytical model`
az datamodel create
    -n ServiceProviderSM2
    --model-directives ServiceProviderAM.json
    -g 'rg-cpd-data-dev-we-02'
    --synapse-workspace 'snp-cpd-data-dev-we-02'