[[_TOC_]]
# Recommended Configurations:
- Size - Standard_D8s_v3
- OS Disk Size - atleast 256 GB
- Data Disk Count - 3 (128 GB each)
- OS - Windows Server 2019 (latest)
- Virtual Network - vnet-cph-pltf-prd-we-01

# Capabilities:
1. [Visual Studio Enterprise 2019 (v16.8.x)](https://github.com/actions/virtual-environments/blob/main/images/win/Windows2019-Readme.md#visual-studio-enterprise-2019)  - Install all the workloads
1. Azure CLI - 2.16.0
1. Azure DevOps CLI extension 0.18.0
1. Powershell 7
1. Android SDK Build Tools - 30.0.3
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

###Powershell Modules Update:
1. Open Powershell in Admin mode and run below commands:
`Install-Module -Name PackageManagement -Repository PSGallery -Force`
`Install-Module -Name PowerShellGet -Repository PSGallery -Force
`
2. Close this shell and open a new one again in admin mode:
`
Install-Module -Name AzureRM.Search -AllowClobber -AllowPrerelease -Force
`

# Notes:
1. VM should have atleast 100 GB of extra OS disk space
2. Clean up the disks on regular intervals to avoid space issues during runtime
3. Update the VM and agents on regular intervals

# References:
https://github.com/actions/virtual-environments

# VM Update Notes:
Mobile Environment Upgrade:
1. Update Visual Studio Installer & Visual Studio to latest in VM.
2. Open Tools=>Android => SDK Manager, download and install the following.(Use the settings button at the bottom to change the repository from "Approved List" to "Full List" to see additional options)
![Change-Repository.jpg](/.attachments/Change-Repository-502cbec8-8523-451f-9ba6-d75a566ef34b.jpg)
   a. from Platforms tab choose API 30 (Android 11 R, Android 11 S). 
![Android-SDK-Platform.jpg](/.attachments/Android-SDK-Platform-22adff21-04c9-4921-8881-d4be458be058.jpg)
   b. from Tools tab, expand build tools and choose Android SDK Build Tools 30.x.x (series)
![Android-Build-Tools.jpg](/.attachments/Android-Build-Tools-c32244d8-7c06-46f0-b513-c7a0c7a0a945.jpg)
