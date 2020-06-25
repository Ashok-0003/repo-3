
# Security Groups:

|Group Name|Description  |
|--|--|
| ms-app-devs | Application Developers |
| ms-app-testers |Application Testers  |
| ms-data-devs | Data Developers |
| ms-data-testers | Data Testers |
| ms-leads | Leads |
| ms-managers | Project Managers |
| ms-architects | Architects |
|ms-infra-devs  | Infra Developers |
| ms-cpd-admins | Azure Resource Admins |
| ms-cpd-all | Development Subscription All Users |
| ms-cph-all | Hub Subscription All User |
| ms-cph-admins |Hub Subscription Admins  |
| ms-cpp-all | Production Subscription All Users |
|  ms-cpp-readers |Production Subscription Readers  |

- Any new security group for Microsoft users should be added to [security-groups.csv](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC%2Fgroups%2Fsecurity-groups.csv) in infra repo
- Any new member should be added to their respective group file in [add members](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC%2FaddMembers)

# Access Levels:
Two scopes of access: resource group and subscription.
1. Reader access to all in production subscription
1. Leads and Architects have contributor access on all resource groups
1. Developers have contributor access on sandbox and dev environment resource groups
1. Test team members have contributor access on test environment resource groups.
1. Infra team members have contributor access on networking resources.
1. Admins have owner access on the subscription


# Addition of new resource groups:
1. Deploy new resource groups through pipelines
1. Update the scripts to include new resource groups for Microsoft users RBAC.
For Central Platform Development resource groups, refer file - [cpd-rbac-mapping.csv](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC%2Froleassignments%2Fcpd-rbac-mapping.csv)
For Central Platform Hub resource groups, refer file - [cph-rbac-mapping.csv](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC%2Froleassignments%2Fcph-rbac-mapping.csv)

#Subscription Level Access
[subscription-rbac-mapping.csv](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC%2Froleassignments%2Fsubscription-rbac-mapping.csv)


## Additional links:
[Path for Interal RBAC Scripts](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_git/infra?path=%2FScripts%2FInternalRBAC) 
