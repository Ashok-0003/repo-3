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






