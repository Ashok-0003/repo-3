# Steps for establishing an Automation Account-

## Prerequisites -

	• A Service Principal with a thumbprint certificate.
	• Two variations for the thumbprint certificate :
		1. cer file to be uploaded in the app registration>certificates & secrets.
		2. pfx file with the private key to be uploaded in the automation account>certificates.
	• Service Principal can have a contributor level access :
		• At the Resource Group level. [OR]
		• At Resource level which is to be managed by the Automation Account.[Recommended]
	
## Configuring the Automation Account -

	• Automation Account> Shared Resources> Connections - 
		• Create a connection with the service principal details.
	• Automation Account> Shared Resources> Certificates -
		• Upload the thumbprint certificate (.pfx) and give it the same name as the connection.
	
## Importing the required modules - 

	• Automation Account> Shared Resources> Module Gallery -
		1. Import Az.Accounts module.
		2. Import Az.Sql module.
		3. Import Az.Synapse module.
		4. Import Az.Kusto module.
     
	Note- Az.Accounts module has to be imported first and it's status should be available before importing the other modules.
	
## Creating the runbooks -

	• Automation Account> Process Automation> Runbooks -
		• Import a runbook will upload the automation scripts in the automation account.
	• A runbook can be configured according to the connection [service principal] -
		• Open the runbook> click on edit - 
			• In the script, change the connection name here -
			 $servicePrincipalConnection=Get-AutomationConnection -Name "Give your connection name"
		• Save and publish the runbook.

## Steps for executing the Scripts -

	• A runbook can be executed by clicking on start.
	• The output can be monitored in the jobs section.

## Creating a Schedule -

	• Automation Account> Shared Resources> Schedules -
		• Click on Add Schedule and configure the schedule accordingly [ Start time, Time zone, Recurring].
	• A schedule can now be linked to a runbook which is to be executed in a timely order without manually running it.
