[[_TOC_]]
# Listing User PAT
https://dev.azure.com/TASMUCP/_usersSettings/tokens

# Pipelines

| Pipeline | Variable | Expiring On | Permissions |User|
|--|--|--|--|--|
|[CD-PlatformAPIs-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=141)|System.NugetAccessToken|15th Jun, 2022|Packaging (Read)| Santosh Nair |
|[CD-WebApps-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=130)|System.NugetAccessToken|15th Jun, 2022|Packaging (Read)| Santosh Nair |
|[CD-PlatformAPIs-Prd-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1021)|System.NugetAccessToken|15th Jun, 2022|Packaging (Read)| Santosh Nair |
|[CD-WebApps-Prd-Release](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1020)|System.NugetAccessToken|15th Jun, 2022|Packaging (Read)| Santosh Nair |


# Agent Pools

|Agent Pool| Expiring On  | Permissions | User  |
|--|--|--|--|
|[platformapispool](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=112&view=jobs)| 15th Jun, 2022 | Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[testagentpool](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=50&view=agents)| -- This has been replaced with tasmumsagents -- |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[webappspool](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=111&view=agents)| 15th Jun, 2022 |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[datapool](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=113&view=agents)| 15th Jun, 2022 |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[tasmumsagents](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=11&view=agents)| 15th Jun, 2022 |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[tasmumsiagents](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=217&view=agents)| 15th Jun, 2022 |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
|[tasmumsagents](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/agentqueues?queueId=217&view=agents)| 15th Jun, 2022 |Agent Pools (Read & manage); Deployment Groups (Read & manage)| Santosh Nair |
# Service Connections


|Connection Name| Expiring On | Permission | User |
|--|--|--|--|
|[ServicesBuildEndPoint](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_settings/adminservices?resourceId=faa0de55-176a-4f89-b775-5e7d1528be93)| 10th Dec, 2021 |Full Access| Paritosh Kumar |

# PR Decorator in Sonar
|Sonar Template| Expiring On | Permission | User |
|--|--|--|--|
| TASMUCP_platform-apis_PR_master | 10th Dec, 2021 | Full Access| Paritosh Kumar |

Raise a ticket with https://aka.ms/servicesdevopsrequest to update token of TASMU Project template used for PR decorations.




