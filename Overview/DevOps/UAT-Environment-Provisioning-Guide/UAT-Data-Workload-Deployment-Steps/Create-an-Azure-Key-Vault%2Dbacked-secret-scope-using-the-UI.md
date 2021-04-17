 **Create an Azure Key Vault-backed secret scope using the UI**
-  Verify that you have Contributor permission on the Azure Key Vault instance that you want to use to back the secret scope.

- Go to https://<databricks-instance>#secrets/createScope. This URL is case sensitive; scope in createScope must be uppercase.
![image.png](/.attachments/image-29140de3-5375-4f2a-a600-8f67c0f2a582.png)
- Enter the name of the secret scope. Secret scope names are case insensitive.
- Use the Manage Principal drop-down to specify whether All Users have MANAGE permission for this secret scope.
- Enter the DNS Name (for example, https://databrickskv.vault.azure.net/) and Resource ID, for example /subscriptions/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx/resourcegroups/databricks-rg/providers/Microsoft.KeyVault/vaults/databricksKV

_(Optional as alternative to the point above) Create an Azure Key Vault-backed secret scope using the Databricks CLI_
- Create the Azure Key Vault scope: 
_databricks secrets create-scope --scope <scope-name> --scope-backend-type AZURE_KEYVAULT --resource-id <azure-keyvault-resource-id> --dns-name <azure-keyvault-dns-name> --initial-manage-principal users_