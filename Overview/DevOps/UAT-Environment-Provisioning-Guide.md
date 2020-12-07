Estimated duration for completion of the deployment steps per workstream
|SL| Step | Workstream  | Estimated Duration |
|--|--|--|--|
| 1 | Infrastructure Provisioning  | Vnets, RGs, Naming Convention and some other fundamental Infra components | Created at the beginning. If another similar environment needs to be created, follow the BOM file. Estimated duration is 1 or 2 days repeating the IaC templates. |
| 2 | Dynamics 365 Environment Provisioning |  |  |
| 3 | Office 365 Tenant (site) Provisioning |  |  |
| 4 | Applications Provisioning |Application Gateways, APIM, AKS, Storages, Cognitive Services, Integration Resources, Docker Containers (API / App Services), etc. required by the Application workloads |**Overall 16-20 hours** (Manual Configurations: 6-8, Azure Resources Provisioning: 6-8 hours, Application deployment: 2-4 hours)|
| 5 | Data Architecture Components Provisioning|||


