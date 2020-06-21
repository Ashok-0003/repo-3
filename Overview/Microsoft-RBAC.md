# Security Groups:
1. ms-app-devs - Application Developers
1. ms-app-testers - Application Testers
1. ms-data-devs - Data Developers
1. ms-data-testers - Data Testers
1. ms-leads - Leads
1. ms-managers - Project Managers
1. ms-architects - Architects
1. ms-infra-devs - Infra Developers
1. ms-cpd-admins - Azure Resource Admins
1. ms-cpd-all -Development Subscription All Users
1. ms-cph-all - Hub Subscription All Users
1. ms-cph-admins - Hub Subscription Admins
1. ms-cpp-all - Production Subscription All Users
1. ms-cpp-readers - Production Subscription Readers

# Access Levels:
1. Reader access to all in production subscription
1. Leads and Architects have contributor access on all resource groups
1. Developers have contributor access on sandbox and dev environment resource groups
1. Test team members have contributor access on test environment resource groups.
1. Infra team members have contributor access on networking resources.

# Addition of new resource groups:
1. Deploy new resource groups through pipelines
1. Update the scripts to include new resource groups for Microsoft users RBAC.
