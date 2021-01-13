
|Key Vault Name| Name  | Type | How to Retrieve | Remarks|
|--|--|--|--|--|
|kv-cpd-apps-<env>-we-01|Cms-Function-ServiceBusConnectionString| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**|
|kv-cpd-apps-<env>-we-01|Cms-Function-NotificationUrl| Secret |Default(Function Key) Function URL of notify function in func-cpd-apps-intntf-<env>-we-01||
|kv-cpd-apps-<env>-we-01|CDNSettings-StorageAccount| Secret |Connection string of the resource **stcpdshrd<env>we01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FieldServiceServiceBus| Secret |Send,Listen access policy connection string of the resource **sb-cpd-apps-int-<env>-we-01**||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-FileStorageAccount| Secret |Connection string for **stcpdappsstr<env>we01**||
|kv-cpd-apps-<env>-we-01|Crm-CaseManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Case api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-case-management-integration-test</p><p> TEST - spn-crm-case-management-integration-test</p><p> DEV - spn-crm-case-management-integration-dev</p>||
|kv-cpd-apps-<env>-we-01|Crm-Common-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for common dynamic connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-common-integration-test</p><p> TEST - spn-crm-common-integration-test</p><p> DEV - spn-crm-general-integration-dev</p>||
|kv-cpd-apps-<env>-we-01|Crm-ProfileManagement-DynamicsSettings-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for Profile api connection, generate secret from Azure AD app registration.<p> UAT - spn-crm-profile-management-integration-test</p><p> TEST - spn-crm-profile-management-integration-test</p><p> DEV - spn-crm-profile-management-integration-dev</p>||
|kv-cpd-apps-<env>-we-01|ConnectionStrings-IntegrationServiceBus| Secret |Send,Listen access policy connection string of the resource sb-cpd-apps-int-<env>-we-01 for deployment||
|kv-cpd-apps-<env>-we-01|EventGridSettings-DomainKey| Secret |Secret stored in kv-cpd-apps-<env>-we-01 used for Event Grid Domain Key, retrieve value from Azure Event Grid Domain egd-cpd-apps-int-<env>-we-01||
|kv-cpd-apps-<env>-we-01|ManageEventFunction-AzureADOptions-ClientSecret| Secret |Client secret stored in kv-cpd-apps-<env>-we-01 used for ManageEvent Function connection, generate secret from Azure AD app registration.||
|kv-cpd-apps-<env>-we-01|Cms-Function-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint|Self signed certificate|
|kv-cpd-apps-<env>-we-01|Cms-Api-ClientCertificate| Certificate |Certificate used to authenticate to SharePoint|Self signed certificate| 


