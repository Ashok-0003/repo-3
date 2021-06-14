1. Inform Malomatia to provision their own build VMs and plan for migration.
1. If MSI is not able to provision their own VMs for builds, they can plan to migrate to agent pool - _Hosted Windows 2019 with VS2019_
1. Update the agent pools and pipelines to use new ones.
1. Remove Build Virtual Machines and their related resources - data and OS disks, etc used by Microsoft.
    >Central Platform Development
    >-  [rg-cpd-glob-bvm-we-01](https://portal.azure.com/#@tasmusqcp.onmicrosoft.com/resource/subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-glob-bvm-we-01/overview)
    >- All other virtual machines in apps resource groups

    >Central Platform Hub
    >- [bldvmdevwe01](https://portal.azure.com/#@tasmusqcpprod.onmicrosoft.com/resource/subscriptions/d8c326fb-f8b4-4854-a2af-dd55e86f6117/resourceGroups/rg-cph-pltf-bldvms-prd-we-01/providers/Microsoft.Compute/virtualMachines/bldvmdevwe01)
    >- [bldvmdevwe02](https://portal.azure.com/#@tasmusqcpprod.onmicrosoft.com/resource/subscriptions/d8c326fb-f8b4-4854-a2af-dd55e86f6117/resourceGroups/RG-CPH-PLTF-BLDVMS-PRD-WE-01/providers/Microsoft.Compute/virtualMachines/bldvmdevwe02)
    >- [bldvmdevwe03](https://portal.azure.com/#@tasmusqcpprod.onmicrosoft.com/resource/subscriptions/d8c326fb-f8b4-4854-a2af-dd55e86f6117/resourceGroups/rg-cph-pltf-bldvms-prd-we-01/providers/Microsoft.Compute/virtualMachines/bldvmdevwe03)
    >- [bldvmdevwe04](https://portal.azure.com/#@tasmusqcpprod.onmicrosoft.com/resource/subscriptions/d8c326fb-f8b4-4854-a2af-dd55e86f6117/resourceGroups/rg-cph-pltf-bldvms-prd-we-01/providers/Microsoft.Compute/virtualMachines/bldvmdevwe04)
    >- [bldvmdevwe05](https://portal.azure.com/#@tasmusqcpprod.onmicrosoft.com/resource/subscriptions/d8c326fb-f8b4-4854-a2af-dd55e86f6117/resourceGroups/rg-cph-pltf-bldvms-prd-we-01/providers/Microsoft.Compute/virtualMachines/bldvmdevwe05)

1. Uninstall the Microsoft specific ADO extensions:
    >- [Microsoft Security Code Analysis (Unified Support)](https://dev.azure.com/TASMUCP/_settings/extensions?tab=installed&extension=ms-codeanalysis.vss-microsoft-security-code-analysis-devops)
    >- [ServicesDevOps](https://dev.azure.com/TASMUCP/_settings/extensions?tab=installed&extension=EnterpriseServicesDevOpsTeam.BuildTool-Tasks)
    >- [ServicesDevOpsTab](https://dev.azure.com/TASMUCP/_settings/extensions?tab=installed&extension=EnterpriseServicesDevOpsTeam.ServicesCode-BuildReportTab)
    >- [SonarQube](https://dev.azure.com/TASMUCP/_settings/extensions?tab=installed&extension=SonarSource.sonarqube)

1. Remove Microsoft specific service connections
    >- [ServicesBuildEndPoint](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices?resourceId=faa0de55-176a-4f89-b775-5e7d1528be93)
    >- [ServiceSonar-CORP](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices?resourceId=ec940214-bf76-4afd-a2ea-16e9bb43b28a)
    >- [vsogd-bdd-nuget](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices?resourceId=abb77288-1df8-4945-8579-1eb5e2c09fa1)
    >- [Telerik](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices?resourceId=95433af2-3073-4654-bcc7-40d9d720e54a) - Malomatia should plan on their own telerik license as it is being used in Mobile Pipelines.
1. Remove Sonar or Quality Control (QC-) pipelines.
1. Remove Microsoft Users from Azure DevOps and Azure Active Directory.
1. Clean up the temporary cloud resources being used by Microsoft team members.
1. Transfer the [organisation](https://dev.azure.com/TASMUCP/_settings/organizationOverview) owner rights to Malomatia POC.
1. Delete this wiki as the handover activities complete.