Estimated duration for completion of the deployment steps per workstream
|SL| Step | Workstream  | Estimated Duration |
|--|--|--|--|
| 1 | Infrastructure Provisioning  | Vnets, RGs, Naming Convention and some other fundamental Infra components | Created at the beginning. If another similar environment needs to be created, follow the BOM file. Estimated duration is 1 or 2 days repeating the IaC templates. |
| 2 | Dynamics 365 Environment Provisioning | D365 Environment creation from D365 admin portal, add and assign licenses to users, deploy D365 solutions and perform related deployment steps. | **Overall approx 24 hours** 3-4 hours for environment creation, 1 day for user setup (depends on count of users), 6-8 hours for first solution deployment and related steps. |
| 3 | CMS Tenant (site) Configuration| O365 Tenant level configuration including local SPO services configurations|Overall **4-6 hours**|
| 4 | Applications Provisioning |Application Gateways, APIM, AKS, Storages, Cognitive Services, Integration Resources, Docker Containers (API / App Services), etc. required by the Application workloads |**Overall 16-20 hours** (Manual Configurations: 6-8, Azure Resources Provisioning: 6-8 hours, Application deployment: 2-4 hours)|
| 5 | Data Architecture Components Provisioning|Infrastructure UAT deployment (#1) must completed + is a pre-requisite; Similar to synthetic use case, solution components for any other business workload (use cases); Detailed steps are in the Wiki |**1 day** for DAI UAT infrastructure deployment using IaC templates. Afterwards **1 day** for DAI synthetic use case deployment using IaC templates (business workload). **Repeat** business workload for other use cases in the future |
| 6 | CMS Solution deployment and configuration |Provisioning of CSM Site Collections; Provisioning CMS Solution deployment artefacts; Configuration of Azure Resources |Overall **32-40h** including solution deployment and sanity testing |

