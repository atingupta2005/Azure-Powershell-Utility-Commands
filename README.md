# Azure-Powershell-Utility-Commands
To delete all resources from Azure paralally

#### - Below command will remove all the Resource Groups and underlying resources from Azure Account in Parallel:
 - Get-AzResourceGroup | ForEach-Object { Start-Job -InputObject $_ -ScriptBlock { $Input | Remove-AzResourceGroup -Force } }
