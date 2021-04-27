# Workspaces
- Tasmu UAT Smart City Dashboard
- Tasmu Command & Control Center Dashboard UAT

# Data Source Connections
The Power Bi reports are connected to multiple data Sources. 
And in each report multiple tables are added via connection queries linking them to their respective source. This operation is done manually. 
If there is an environment migration for instance, or a a resource change or else, to avoid redundancy of changing manually the connection query of each table, we introduced parameters in Power Bi to dynamically change the data sources. 

## Parameters
A parameter has to be created for every different database and data source.
Currently the value of the parameters : the connection string

 Data Sources
- sql-cpd-data-tst-we-01.database.windows.net
- https://adxcpddatatstwe01.westeurope.kusto.windows.net 

Databases
- smartparking-cpd-adxdb
- sqldb-cpd-data-tst-we-01
- sqldb-cpd-dynamics-data-tst-we-01
- smartcitytst
- costmanagement
![image.png](/.attachments/image-2fdf0348-fba2-4486-8b27-658a80b26255.png)

## M Query
For each table the parameter is introduced in the Advanced editor section. 
- For ADX: 
let
    Source = AzureDataExplorer.Contents([_Datasource Parameter Name_],[_Database Parameter Name]_),
- For Sql:
let
    Source = Sql.Database([_Datasource Parameter Name_],[_Database Parameter Name]_),

## Other possibility
For Sql Data sources only, a quicker change can be made without having to edit every M query of every table : 
In the Data Source Settings -> Change Source -> in Server & Database chose the Parameter in question.
![image.png](/.attachments/image-5042b20e-a27e-4a46-9706-b454c8825aa3.png)

## Options and Settings
This option has to be chosen in order for the dynamic sources to be working. 

![image.png](/.attachments/image-0f5e4cb8-f8cf-4ed5-a5f8-c65df3814544.png)

## Next Steps

Once the Parameters are implemented, the M queries are changed and the parameterization option is selected in Power BI, if there is any data source or database change, only the parameters have to be changed, and it will update the queries for all the tables. 
They might be a necessity to enter the credentials of the new data sources if any, for the  tables to be working fine. 