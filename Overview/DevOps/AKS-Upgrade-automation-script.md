The below script is for reviewing and upgrading AKS

<#
.SYNOPSIS
    Perform Azure Kubernetes Cluster and Node Upgrade

.DESCRIPTION
    This PowerShell script helps to automate/perform AKS upgrade. The script fetch the available
    AKS version in a particular region, prompts to enter the version to upgrade and based on the version
    entered by the user, AKS Cluster and Nodes will upgrade to the specified version.

    The Script can be run in two ways:
    1. By specifying the parameters on the prompts
    2. Not specifying the parameters. This will prompt you to enter the Subscription, Resource Group, AKS Cluster Name,
       and Tenant ID.
    Note: The script requires the correct input of Subscription Name, TenantID, Resource Group, and AKS Cluster Name to function.


.EXAMPLE
    .\AKS_UpgradeScript-Prod.ps1 -Subscription "Subscription Name" -TenantID "xxx-xxxxx-xxxxxx-xxxxx"
    -ResourceGroup "resource group name" -AKSClusterName "Aks Cluster Name"

.EXAMPLE
    .\AKS_UpgradeScript-Prod.ps1

.NOTES
    Author: Moses Adonteng | LICENSE Copyright 2023

.PARAMETER Subscription
    The subscription name where the AKS cluster and nodes resides

.PARAMETER TenantID
    The AzureAD Tenant ID

.PARAMETER ResourceGroup
    The Resource Group of the AKS Cluster

.PARAMETER AKSClusterName
    The AKS Cluster Name

.PARAMETER AKSVersionToUpgrade
    The AKS version to upgrade to. If not specified, the user will be prompted to enter the version.
 
.PARAMETER UpgradeSuccessfulMsg
    A message to display upon successful upgrade. If not specified, a default message will be used.
 
.PARAMETER versionAvailableToUpgrade
    An array list of available AKS versions to upgrade to. If not specified, the script will fetch available versions.
 
.PARAMETER versionAvailable
    The available AKS versions to upgrade to. If not specified, the script will fetch available versions.
 
.PARAMETER getAKSCredentials
    An object to store AKS cluster credentials. If not specified, the script will fetch and store credentials.
 
.PARAMETER checkIfVersionFound
    A boolean parameter to check if the version specified is available. If not specified, it will not be checked.
 
.PARAMETER checkParameterDefined
    A boolean parameter to check if all required parameters are defined. If not specified, it will not be checked.
 
.PARAMETER checkSuccessfullAuthentication
    A parameter to check if authentication was successful. If not specified, it will not be checked.
 
.PARAMETER userOutputResult
    An object to store the results of the script. If not specified, it will be an empty array.

.INPUTS 
    None

.OUTPUTS
    None
 
.FUNCTIONALITY
    Automates the process of upgrading AKS cluster and nodes.
 
.NOTES
    This script requires the Azure CLI to be installed and configured before use.


#>
[CmdletBinding()]
    param (
        [string]$Subscription,
        [string]$TenantID,
        [string]$ResourceGroup,
        [string]$AKSClusterName,
        [string]$AKSVersionToUpgrade,
        [string]$UpgradeSuccessfulMsg,
        [System.Collections.ArrayList]$versionAvailableToUpgrade=@(),
        [string]$availableVersions,
        [PSCustomObject]$getAKSCredentials=@{},
        [bool]$checkIfVersionFound = $false,
        [PSCustomObject]$userOutputResult = @{}


    )

function Get-SubscriptionDetails {
    Write-Host "Please Enter the Below Details As required:"  
    Start-Sleep -Seconds 2      
    try {
            $Subscription = Read-Host "Enter the Subscription Name: "
            $TenantID = Read-Host "Enter the Tenant ID: "
            $ResourceGroup = Read-Host "Enter AKS Resource Group Name: "
            $AKSClusterName = Read-Host "Enter the AKS Cluster Name: "
            $userInputresult = validateUserCommandLineInput -Subscription $Subscription -TenantID $TenantID -ResourceGroup $ResourceGroup -AKSClusterName $AKSClusterName
    }
    catch {
        Write-Error $PSItem.Exception.Message
        break
    }    
   
   return $userInputresult
}

# Get AKS Version Available in West Europe
function Get-AvailableAKSVersion {
    param (
        [PSCustomObject]$userObject
    )
    try {
            # Get the Azure AKS Cluster Credentials
            $null= az aks get-credentials -g $userObject.ResourceGroup -n $userObject.AKSClusterName --overwrite-existing

            # List the AKS Version Available within the Region
            $availableVersions = az aks get-upgrades --resource-group $userObject.ResourceGroup --name $userObject.AKSClusterName --output table
    }
    catch {
        Write-Error $PSItem.Exception.Message
        break
    }
     
    return $availableVersions
   
}

# Get Azure Authentication Details
function Get-AzureAuthenticationDetails {
    [CmdletBinding()]
    param (
         [PSCustomObject]$userObject
    )
     try {
             # Connect to AZ Login
             $null = az login
 
             # Connect to Azure Account
             $null = Connect-AzAccount -Tenant $userObject.TenantID -SubscriptionId $userObject.Subscription
 
             # Check Authorization Details
             #Get-AzureAuthorizationDetails -accountLoginContext $azureAccountLogin.Context.Name
             # Set Account
             $null = az account set --subscription $userObject.Subscription
 
             # Set Azure Context
             $null = Set-AzContext -Subscription $userObject.Subscription
     }
     catch {
         Write-Error $PSItem.Exception.Message
         break
     }
     
 }
 
# Validate the User Input from the CommandLine
function validateUserCommandLineInput {
    param (
        [string]$Subscription,
        [string]$TenantID,
        [string]$ResourceGroup,
        [string]$AKSClusterName
    )
    if($Subscription -ne "" -and $TenantID -ne "" -and $ResourceGroup -ne "" -and $AKSClusterName -ne ""){
        $userInputresult = @{
            "Subscription" = $Subscription
            "TenantID" = $TenantID
            "ResourceGroup" = $ResourceGroup
            "AKSClusterName" = $AKSClusterName
       }
    }
    else {
        Write-Error $PSItem.Exception.Message
        break
    }
    return $userInputresult
}


function Get-AzureAuthorizationDetails {
    param (
        $accountLoginContext
    )
    if($null -eq $accountLoginContext){
        Write-Output "Don't have the necessary permission on the Azure AKS Resource"
        break
    }
}


# Function to perform the Upgrade
function performAKSUpgrade {
    param (
        $versionAvailableToUpgrade
    )
    try {
            # Get the version number you want to update to
            $AKSVersionToUpgrade = Read-Host "Enter the AKS Version you want to Upgrade"
    }
    catch {
        Write-Error $PSItem.Exception.Message
    }
   

    # Check if the value is entered and its not null
    if ($AKSVersionToUpgrade -ne "")
    {
        foreach($ver in $versionAvailableToUpgrade)
        {
            if($ver -eq $AKSVersionToUpgrade)
            {
                $checkIfVersionFound = $true
                break
            }
           
        }
        if($checkIfVersionFound){
                Write-Output "The Version is Valid and available within the Region"
                Start-Sleep -Seconds 5
                Write-Output "Starting Update Process"
                Start-Sleep -Seconds 2
                try {
                        #az aks upgrade --resource-group $ResourceGroup --name $AKSClusterName --kubernetes-version $AKSVersion --yes
                }
                catch {
                        Write-Error $PSItem.Exception.Message
                }
               
                Write-Output "Update Completed Successfully"
               
        }
        else {
                Write-Output "Version entered is not Valid!!!"
        }    
       
    }
    else {
        Write-Error -Message "Please Enter the AKS Version you want to upgrage"
    }
}

if(!($PSBoundParameters.ContainsKey("AKSClusterName") -and $PSBoundParameters.ContainsKey("Subscription") -and $PSBoundParameters.ContainsKey("TenantID") -and $PSBoundParameters.ContainsKey("ResourceGroup")))
{
    $userOutputResult = Get-SubscriptionDetails
}
else {
    $userOutputResult = @{
        "Subscription" = $Subscription
        "TenantID" = $TenantID
        "ResourceGroup" = $ResourceGroup
        "AKSClusterName" = $AKSClusterName
    }
}

try {
        # Authenticate and Set Az Context
        Get-AzureAuthenticationDetails -userObject $userOutputResult

        # Call the Get-AvailableAKSVersion
        $displayVersions = Get-AvailableAKSVersion -userObject $userOutputResult

        # Display the Versions
        Write-Output $displayVersions

        # Split the Upgrade into a List
        $versionAvailableToUpgrade = $displayVersions[2].Replace(" ", "").substring(38).split(",")

        # Perform AKS Upgrade
        performAKSUpgrade $versionAvailableToUpgrade
}
catch {
        Write-Error $PSItem.Exception.Message
}
