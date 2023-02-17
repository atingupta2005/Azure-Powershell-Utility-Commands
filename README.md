# Azure-Powershell-Utility-Commands
To delete all resources from Azure paralally

### Set Subscription
- az account set --subscription "S-06-10"

#### - Below command will remove all the Resource Groups and underlying resources from Azure Account in Parallel:
 - Get-AzResourceGroup | ForEach-Object { Start-Job -InputObject $_ -ScriptBlock { $Input | Remove-AzResourceGroup -Force } }


#### Reset Password
 - az ad user update  --force-change-password-next-sign-in false  --id u01@atinkhoutlook.onmicrosoft.com  --password <password>
