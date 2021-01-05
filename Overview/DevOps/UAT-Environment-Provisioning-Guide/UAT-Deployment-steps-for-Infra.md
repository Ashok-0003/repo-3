# Infra Components Deployment Sequence
Infra components are grouped into two main categories:
1. Infra functions. These functions and their associated resource groups are listed below:
* Monitoring: rg-*-mon-*
* Security: rg-*-sec-*
* Networking: rg-*-net-*
* Backup and Recovery: rg-*-bckup-*

2. Infra workloads are workloads like FWs, ADDS and DNS services to support the platform. Each workload exists in dedicated resource groups such like:
* ADDS: rg-*-adds-*
* DNSProxy: rg-*-dnsp-*
* FW Ingress: rg-*-fwin-*

Please note that for each RG deployment there exists a dedicated deployment pipeline to deploy that RG and associated resources within.
While deploying the landing zone, Infra functions should be deployed prior to the infra workloads or any other platform workloads since most of the workloads depend on existence of infra functions such as Virtual Network, Azure Monitor etc.

While deploying the infra functions following sequence can be used:
1. -mon- RGs 
* LogAnalytics worksplaces deployed in the mon RGs are referenced by NSGs and other components in their IaC definition to enable monitoring during the deployment. Because of this reason mon RG should be deployed before the sec RG
2. -sec- RGs
* NSGs located in the sec RGs will be referenced during the Virtual Network deployment. Because of this reason sec RG should be deployed before the net RG
3. -net- RGs
* RouteTables and VirtualNetwork deployments both exist in the net RGs. However RouteTables should be deployed before the VirtualNetwork. To ensure this sequencing, 'dependsOn' property is used in the deployment template file. This guarantees Virtual Network deployment dependsOn RouteTables deployment. Additionally NSGs are referenced during the VirtualNetwork deployment, thus ensuring sec RGs are deployed prior to the net RG mitigates the potential deployment failure
4. -bckup- RGs
* Recovery Services Vaults might be referenced by the infra/platform workloads during their deployments. Because of this reason bckup RGs should be deployed before the workload RGs
5. <infra workload> RGs
6. <platform workload> RGs



[TASMU Landing Zone BOM.xlsx](/.attachments/TASMU%20Landing%20Zone%20BOM-0a24bf9d-e274-40c8-addf-3a93c99166ff.xlsx)

As it is shown in the attached "Tasmu Landing Zone Bom.xlsx" file, UAT and other environments networks created based on pre-defined Vnets/Subnets and IP allocations.
IP allocations were checked with MOTC and Microsoft CSU team so that all the environment networks are properly defined and vnets/subnets are created. 

Also, as it is explained in the BOM file, UAT environment naming convention is defined for all resource groups and resources. It is expected from all developers to follow naming convention for any deployments.

Because of all development environments sits in the same development subscription, they can all use shared infra services like; Firewall, key vaults, storages etc.

Below is just an example on how to deploy Vnets vie IaC. For more information, please refer to repos for all Infra as Codes and ARM templated.

{
    "$schema": "https://schema.management.azure.com/schemas/2019-04-01/deploymentTemplate.json#",
    "contentVersion": "1.0.0.0",
    "parameters": {
        "vNetName": {
            "type": "string",
            "metadata": {
                "description": "Required. The Virtual Network (vNet) Name."
            }
        },
        "location": {
            "type": "string",
            "defaultValue": "[resourceGroup().location]",
            "metadata": {
                "description": "Optional. Location for all resources."
            }
        },
        "vNetAddressPrefixes": {
            "type": "array",
            "metadata": {
                "description": "Required. An Array of 1 or more IP Address Prefixes for the Virtual Network."
            }
        },
        "subnets": {
            "type": "array",
            "minLength": 1,
            "metadata": {
                "description": "Required. An Array of subnets to deploy to the Virual Network."
            }
        },
        "dnsServers": {
            "type": "array",
            "defaultValue": [],
            "metadata": {
                "description": "Optional. DNS Servers associated to the Virtual Network."
            }
        },
        "ddosProtectionPlanId": {
            "type": "string",
            "defaultValue": "",
            "metadata": {
                "description": "Optional. Resource Id of the DDoS protection plan to assign the VNET to. If it's left blank, DDoS protection will not be configured. If it's provided, the VNET created by this template will be attached to the referenced DDoS protection plan. The DDoS protection plan can exist in the same or in a different subscription."
            }
        },
        "diagnosticLogsRetentionInDays": {
            "type": "int",
            "defaultValue": 365,
            "minValue": 0,
            "maxValue": 365,
            "metadata": {
                "description": "Optional. Specifies the number of days that logs will be kept for; a value of 0 will retain data indefinitely."
            }
        },
        "diagnosticStorageAccountId": {
            "type": "string",
            "defaultValue": "",
            "metadata": {
                "description": "Optional. Resource identifier of the Diagnostic Storage Account."
            }
        },
        "workspaceId": {
            "type": "string",
            "defaultValue": "",
            "metadata": {
                "description": "Optional. Resource identifier of Log Analytics."
            }
        },
        "eventHubAuthorizationRuleId": {
            "type": "string",
            "defaultValue": "",
            "metadata": {
                "description": "Optional. Resource ID of the event hub authorization rule for the Event Hubs namespace in which the event hub should be created or streamed to."
            }
        },
        "eventHubName": {
            "type": "string",
            "defaultValue": "",
            "metadata": {
                "description": "Optional. Name of the event hub within the namespace to which logs are streamed. Without this, an event hub is created for each log category."
            }
        },
        "lockForDeletion": {
            "type": "bool",
            "defaultValue": true,
            "metadata": {
                "description": "Optional. Switch to lock Virtual Network from deletion."
            }
        },
        "tags": {
            "type": "object",
            "defaultValue": {},
            "metadata": {
                "description": "Optional. Tags of the Virtual Network resource."
            }
        }
    },
    "variables": {
        "subnetNamesToOutput": {
            "copy": [
                {
                    "name": "subnetNamesOutput",
                    "count": "[length(parameters('subnets'))]",
                    "input": "[parameters('subnets')[copyIndex('subnetNamesOutput')].name]"
                }
            ]
        },
        "subnetIdsToOutput": {
            "copy": [
                {
                    "name": "subnetIdsOutput",
                    "count": "[length(parameters('subnets'))]",
                    "input": "[resourceId('Microsoft.Network/virtualNetworks/subnets', parameters('vNetName'), parameters('subnets')[copyIndex('subnetIdsOutput')].name)]"
                }
            ]
        },
        "dnsServers": {
            "dnsServers": "[array(parameters('dnsServers'))]"
        },
        "ddosProtectionPlan": {
            "id": "[parameters('ddosProtectionPlanId')]"
        },
        "diagnosticsMetrics": [
            {
                "category": "AllMetrics",
                "timeGrain": null,
                "enabled": true,
                "retentionPolicy": {
                    "enabled": true,
                    "days": "[parameters('diagnosticLogsRetentionInDays')]"
                }
            }
        ],
        "diagnosticsLogs": [
            {
                "category": "VMProtectionAlerts",
                "enabled": true,
                "retentionPolicy": {
                    "enabled": true,
                    "days": "[parameters('diagnosticLogsRetentionInDays')]"
                }
            }
        ]
    },
    "resources": [
        {
            "type": "Microsoft.Network/virtualNetworks",
            "apiVersion": "2019-04-01",
            "name": "[parameters('vNetName')]",
            "location": "[parameters('location')]",
            "tags": "[parameters('tags')]",
            "properties": {
                "addressSpace": {
                    "addressPrefixes": "[parameters('vNetAddressPrefixes')]"
                },
                "ddosProtectionPlan": "[if(not(empty(parameters('ddosProtectionPlanId'))), variables('ddosProtectionPlan'), json('null'))]",
                "dhcpOptions": "[if(empty(parameters('dnsServers')), json('null'), variables('dnsServers'))]",
                "enableDdosProtection": "[not(empty(parameters('ddosProtectionPlanId')))]",
                "copy": [
                    {
                        "name": "subnets",
                        "count": "[length(parameters('subnets'))]",
                        "input": {
                            "name": "[parameters('subnets')[copyIndex('subnets')].name]",
                            "properties": {
                                "addressPrefix": "[parameters('subnets')[copyIndex('subnets')].addressPrefix]",
                                "networkSecurityGroup": "[if(empty(parameters('subnets')[copyIndex('subnets')].networkSecurityGroupName), json('null'), json(concat('{\"id\": \"', resourceId(parameters('subnets')[copyIndex('subnets')].nsgsRGName,'Microsoft.Network/networkSecurityGroups', parameters('subnets')[copyIndex('subnets')].networkSecurityGroupName), '\"}')))]",
                                "routeTable": "[if(empty(parameters('subnets')[copyIndex('subnets')].routeTableName), json('null'), json(concat('{\"id\": \"', resourceId(parameters('subnets')[copyIndex('subnets')].routesRGName,'Microsoft.Network/routeTables', parameters('subnets')[copyIndex('subnets')].routeTableName), '\"}')))]",
                                "serviceEndpoints": "[if(empty(parameters('subnets')[copyIndex('subnets')].serviceEndpoints), json('null'), parameters('subnets')[copyIndex('subnets')].serviceEndpoints)]",
                                "delegations": "[if(contains(parameters('subnets')[copyIndex('subnets')], 'delegations'), if(empty(parameters('subnets')[copyIndex('subnets')].delegations), json('null'), parameters('subnets')[copyIndex('subnets')].delegations), json('null'))]",
                                "privateEndpointNetworkPolicies": "Disabled",
                                "privateLinkServiceNetworkPolicies": "Enabled"
                            }
                        }
                    }
                ]
            },
            "resources": [
                {
                    "type": "providers/locks",
                    "apiVersion": "2016-09-01",
                    "condition": "[parameters('lockForDeletion')]",
                    "name": "Microsoft.Authorization/virtualNetworkDoNotDelete",
                    "dependsOn": [
                        "[resourceId('Microsoft.Network/virtualNetworks/', parameters('vNetName'))]"
                    ],
                    "comments": "Resource lock on virtual network",
                    "properties": {
                        "level": "CannotDelete"
                    }
                },
                {
                    "type": "Microsoft.Network/virtualNetworks/providers/diagnosticsettings",
                    "apiVersion": "2017-05-01-preview",
                    "name": "[concat(parameters('vNetName'), '/Microsoft.Insights/service')]",
                    "location": "[parameters('location')]",
                    "condition": "[or(not(empty(parameters('diagnosticStorageAccountId'))),not(empty(parameters('workspaceId'))),not(empty(parameters('eventHubAuthorizationRuleId'))),not(empty(parameters('eventHubName'))))]",
                    "dependsOn": [
                        "[concat('Microsoft.Network/virtualNetworks/', parameters('vNetName'))]"
                    ],
                    "properties": {
                        "storageAccountId": "[if(empty(parameters('diagnosticStorageAccountId')), json('null'), parameters('diagnosticStorageAccountId'))]",
                        "workspaceId": "[if(empty(parameters('workspaceId')), json('null'), parameters('workspaceId'))]",
                        "eventHubAuthorizationRuleId": "[if(empty(parameters('eventHubAuthorizationRuleId')), json('null'), parameters('eventHubAuthorizationRuleId'))]",
                        "eventHubName": "[if(empty(parameters('eventHubName')), json('null'), parameters('eventHubName'))]",
                        "metrics": "[if(and(empty(parameters('diagnosticStorageAccountId')), empty(parameters('workspaceId')), empty(parameters('eventHubAuthorizationRuleId')), empty(parameters('eventHubName'))), json('null'), variables('diagnosticsMetrics'))]",
                        "logs": "[if(and(empty(parameters('diagnosticStorageAccountId')), empty(parameters('workspaceId')), empty(parameters('eventHubAuthorizationRuleId')), empty(parameters('eventHubName'))), json('null'), variables('diagnosticsLogs'))]"
                    }
                }
            ]
        }
    ],
    "outputs": {
        "vNetResourceGroup": {
            "type": "string",
            "value": "[resourceGroup().name]",
            "metadata": {
                "description": "The name of the Resource Group the Virtual Network was created in."
            }
        },
        "vNetResourceId": {
            "type": "string",
            "value": "[resourceId('Microsoft.Network/virtualNetworks', parameters('vNetName'))]",
            "metadata": {
                "description": "The Resource id of the Virtual Network deployed."
            }
        },
        "vNetName": {
            "type": "string",
            "value": "[parameters('vNetName')]",
            "metadata": {
                "description": "The name of the Virtual Network deployed."
            }
        },
        "subnetNames": {
            "type": "array",
            "value": "[variables('subnetNamesToOutput').subnetNamesOutput]",
            "metadata": {
                "description": "The Names of the Subnets deployed to the Virtual Network."
            }
        },
        "subnetIds": {
            "type": "array",
            "value": "[variables('subnetIdsToOutput').subnetIdsOutput]",
            "metadata": {
                "description": "The Resource Ids of the Subnets deployed to the Virtual Network."
            }
        }
    },
    "functions": []
}
