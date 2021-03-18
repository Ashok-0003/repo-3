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

## Landing Area :
- Dev LandingZone: stlandingzonedevwe01

_Notes:_ 
_- Files to be processed are to be stored "KPI" root folder_

## Databricks
- Name : db-cpd-datat-dev-we-01
- Notebooks : **Settings** & **SchemaAndDQConformancyCheck**

_Notes :_ 
_- Mandatory parameters : **file_name_purview, file_to_check, sector**_

Line to be modified to integrate another sector (zone to be mounted):
`folder = "/mnt/landingzone/purviewhealthcare/KPI/"`

## SQL :
- Server name : sql-cpd-data-demo-dev-we-01.database.windows.net
- Database name : sqldb-cpd-data-demo-dev-we-01

_Notes :_
_- Rules are stored in table dq.kpiRules_
_- Entity name must match entity name in Purview_

## PowerBI Reports
- Name : MscTasmuDataQualityDemo
- Connected to SQL server sql-cpd-data-demo-dev-we-01 (see above)
