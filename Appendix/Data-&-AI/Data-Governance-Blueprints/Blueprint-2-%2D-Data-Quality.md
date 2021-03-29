# Data Flow :
![image.png](/.attachments/image-0a130ec8-8b34-49ae-b581-2f2c145a32b4.png)

# Resources : 
## Azure Data Factory : 
- Name : adf-cpd-data-dev-we-07
- Pipeline : PurviewDataQuality

## Purview 
- Name : purv-cpd-data-dev-we-01

_Notes :_
_- Entities must have "MasterData" classification_ 
_- Naming conventions must be respected (ex: "HLT" prefix for Healthcare sector)_

## Key Vault
- Name : kv-cpd-data-dev-we-01
- Secrets used for Purview : *purview-clientId, purview-clientSecret & purview-tenantId*
- Secrets used for SQL : *demoPurview-SqlUser* & *demoPurview-SqlPassword*

Storing secrets for Purview & SQL connections

## Landing Area :
- Dev LandingZone: stlandingzonedevwe01

_Notes:_ 
_- Files to be processed are to be stored "KPI" root folder_
_- Files must respect naming conventions (with sector prefix and date ; ex: HLT_002_National inventory of medical supply_2020-10-29.csv)_

## Databricks
- Name : db-cpd-datat-dev-we-01
- Notebooks : **Settings** & **SchemaAndDQConformancyCheck**
- Mandatory libraries : pyspark-check & spark_mssql_connector_2_12_3_0_1_0_0_alpha

_Notes :_ 
_- Mandatory parameters : **file_name_purview, file_to_check, sector**_
_- You can download your jar files to install the libraries [here](https://search.maven.org/)_

Line to be modified to integrate another sector (zone has to be mounted beforehand):
`folder = "/mnt/landingzone/purviewhealthcare/KPI/"`

## SQL :
- Server name : sql-cpd-data-demo-dev-we-01.database.windows.net
- Database name : sqldb-cpd-data-demo-dev-we-01

_Notes :_
_- Rules are stored in table dq.kpiRules_
_- Entity name must match entity name in Purview_
_- Ensure that your IP address is allowed or that Azure Services can access the databases_


## PowerBI Reports
- Name : MscTasmuDataQualityDemo
- Connected to SQL server sql-cpd-data-demo-dev-we-01 (see above)
