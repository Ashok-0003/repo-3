May 24 2022 
Specific to AKS upgrade from V 1.21 to 1.22

**Prerequisites**
- Permissions – Contributor on the AKS resource group 
- Virtual machine – on a VNET that is peered with the VNET that AKS resides on. For our upgrades we use VM bldvmprewe01.
- For AzureCLI, kubectl and helm : follow the steps at [https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_wiki/wikis/TASMU-Central-Platform.wiki/113/Debugging-Guide?anchor=using-command-line]()

**Steps**
- Access the virtual machine
- Open PowerShell as Administrator
- Use “az login” to login
- 




