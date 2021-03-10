# Deployment of Synapse database views
1. Connect to snp-cpd-data-<ENV>-we-01-ondemand.sql.azuresynapse.net with Synapse Workspace Studio or with a SQL client of your choice
1. Run queries described in /ServiceProvider/BillingSynapseQueries.sql, with manual steps as described inline
1. Please note that Synapse Workspace connects to the Gold Zone datalake with Shared Access Signature, which has an expire date.

# Setup of Power BI Embed
1. Create a new Service Provider Workspace and call it for example Tasmu Service Provider <Env>
1. follow the steps outlined in the following article [https://docs.microsoft.com/en-us/power-bi/developer/embedded/embed-service-principal](Embed Power BI content with service principal and an application secret)
2. Assign the Azure Embedded capacity to the workspace

![image.png](/.attachments/image-dbb55f33-cf18-476a-bd34-a482dac837a2.png)

# Deployment of Service Provider Reports
There are two reports that are required to be deployed to the new workspace
1. ServiceProviderBilling
One report will display the billing data for the logged in user from the Apps portal. The Apps portal passes the ServiceProviderId as part of the integration
1. ServiceHealth
Each new service provider onboarded will have his own report deployed to the workspace with the value of Paramter1 = his log analytics workspace id, as shown below
![image.png](/.attachments/image-69a329a2-36eb-416a-83bd-88a95e60a8c7.png) 