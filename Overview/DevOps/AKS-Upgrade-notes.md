May 24 2022 
Specific to AKS upgrade from V 1.21 to 1.22

**Prerequisites**
- Permissions – Contributor on the AKS resource group 
- Virtual machine – on a VNET that is peered with the VNET that AKS resides on. For our upgrades we use VM bldvmprewe01.
- For AzureCLI, kubectl and helm : follow the steps at [https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/113/Debugging-Guide?anchor=using-command-line]()
- The Service Principal per environment (in this case dev) : spn-apps-aks-**dev** should have the following permissions
- [ ] privatelink.westeurope.azmk8s.io = Private DNS Zone Contributor
- [ ] rg-cpd-pltf-net-dev-we-01 = Network Contributor (Required only for the duration of the upgrade)


**Steps**
- Access the virtual machine
- Open PowerShell as Administrator
- Use “az login” to login
- az account set --subscription 'Central Platform Development'
- az aks get-credentials -g rg-cpd-apps-aks-dev-we-01 -n aks-cpd-apps-dev-we-01
## The next command checks the available versions to upgrade to 
- az aks get-upgrades --resource-group rg-**cpd**-apps-aks-**dev**-we-01 --name aks-**cpd**-apps-**dev**-we-01 --output table (Ensure to change the subscription and environment) 
## The next command is to start the upgrade (Ensure to change the subscription and environment)
- az aks upgrade --resource-group rg-**cpd**-apps-aks-**dev**-we-01 --name aks-**cpd**-apps-**dev**-we-01 --kubernetes-version 1.22.6
## This step will take approximately one hour, depending on the number of node pools and nodes. 
## After the upgrade, validate status by checking on the Azure Portal and running
- az aks show --resource-group rg-**cpd**-apps-aks-**dev**-we-01 --name aks-**cpd**-apps-**dev**-we-01 --output table
- Remove the granted Network Contributor permissions
## Validate pod status by running 
- kubectl get pods -n webapps
- kubectl get pods -n apiapps

## With AKS version 1.22, there are changes to the Kubernetes APIs. To work with the new APIs, the Application Gateway Ingress Controller (AGIC) is to be upgraded to the version that is available N-1

- az aks get-credentials -g rg-cpd-apps-aks-dev-we-01 -n aks-cpd-apps-dev-we-01
- helm list -A
- helm repo add application-gateway-kubernetes-ingress https://appgwingress.blob.core.windows.net/ingress-azure-helm-package/
- helm repo update
- kubectl config current-context
- helm uninstall --namespace ingress ingress-azure
### After the below command is run, additional commands are required to set permissions for the AGIC. Install the AGIC first to obtain the AGIC Object ID
- helm install --namespace ingress ingress-azure application-gateway-kubernetes-ingress/ingress-azure --version 1.5.0 --set appgw.applicationGatewayID=/subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-apps-aks-dev-we-01/providers/Microsoft.Network/applicationGateways/agw-cpd-apps-aks-dev-we-01 --set rbac.enabled=true --set appgw.usePrivateIP=true 
- kubectl get pods -n ingress
- kubectl describe pod/_podname_ -n ingress
- kubectl logs pod/_podname_ -n ingress
## Add App GW RG Reader permissions to AGIC (the AGW Resource ID is to be provided)
- az role assignment create --role Reader --scope /subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-apps-aks-dev-we-01 --assignee cba2cb33-6437-49d9-a910-d694acc53a87
## Add App GW contributor permissions to AGIC
- az role assignment create --role Contributor --scope /subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-apps-aks-tst-we-01/providers/Microsoft.Network/applicationGateways/agw-cpd-apps-aks-tst-we-01 --assignee 681c7026-5e34-4dcd-97f0-4861ef847b68
## Add Managed identity operator permissions to AGIC, allowing to control the AGW via the managed identity
- az role assignment create --role "Managed Identity Operator" --scope /subscriptions/d0694def-b27e-4bb7-900d-437fbeb802da/resourceGroups/rg-cpd-apps-aks-tst-we-01/providers/Microsoft.ManagedIdentity/userAssignedIdentities/mi-cpd-apps-agwaks-tst-we-01 --assignee 681c7026-5e34-4dcd-97f0-4861ef847b68 
- Delete the pod by running kubectl delete pod _podname_ -n ingress
- The pod will automatically recreate , you can check status via kubectl get pods -n ingress , status should show running 1/1 
- You can check AKS AGW for status and validate by running health checks after allowing ten minutes for AGW updates. 

## Sanity checks for Development environment 
- visit https://marketplace.dev.sqcp.qa/en/index.html  
- Visit https://api.dev.sqcp.qa/config/api/feature 




