# Recommended Configurations:
- Size - Standard_D8s_v3
- OS Disk Size - 256 GB
- Data Disk Count - 3 (128 GB each)
- OS - Windows Server 2019 (latest)
- Virtual Network - vnet-cph-pltf-prd-we-01

# Capabilities:
1. [Visual Studio Enterprise 2019 (v16.8.x)](https://github.com/actions/virtual-environments/blob/main/images/win/Windows2019-Readme.md#visual-studio-enterprise-2019)  - Install all the workloads
1. Azure CLI - 2.16.0
1. Azure DevOps CLI extension 0.18.0
1. Powershell 7
1. Android SDK Build Tools - 29.0.x
1. Java - 1.8.x
1. Azure PowerShell module 2.1.0 
1. AzureRM PowerShell module 2.1.0 
1. Powershell modules 
Pester	- 5.0.2
PowerShellGet
1. Helm 3.4.x
1. Docker 19.03.13
1. Node 14.15.1
1. Kubectl 1.20.0
1. NuGet 5.8.0.6930
1. NPM 6.14.8
1. Microsoft Edge
1. Google Chrome
1. OpenSSL 1.1.1

Powershell Modules Update:
1. Open Powershell in Admin mode and run below commands:
`Install-Module -Name PackageManagement -Repository PSGallery -Force`
`Install-Module -Name PowerShellGet -Repository PSGallery -Force
`
2. Close this shell and open a new one again in admin mode:
`
Install-Module -Name AzureRM.Search -AllowClobber -AllowPrerelease -Force
`


# Agent Pools:
1. tasmumsagents
2. webappspool
3. platformapispool
4. datapool
5. testagentpool

# Pipelines:
<List to be updated>

# References:
https://github.com/actions/virtual-environments


