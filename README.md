# Azure-Powershell-Utility-Commands
To delete all resources from Azure paralally

### Set Subscription
```
az account set --subscription "S-06-10"
```

#### - Below command will remove all the Resource Groups and underlying resources from Azure Account in Parallel:
```
Get-AzResourceGroup | ForEach-Object { Start-Job -InputObject $_ -ScriptBlock { $Input | Remove-AzResourceGroup -Force } }
```

#### Reset Password
```
az ad user update  --force-change-password-next-sign-in false  --id u01@atinkhoutlook.onmicrosoft.com  --password <password>
```
 
### Delete All Service Principal IDs from AAD:
```
for appId in $(az ad sp list --all --query  [].[appId]  --output tsv); do
  echo $appId
  az ad sp delete --id $appId
done
```

### Delete resource groups
```
az account set --subscription "S-01-05"
for rg in $(az group list --query  [].[name] -o tsv); do
	echo "Deleting resource group - $rg"
	az group delete -n $rg --no-wait --yes
done
```
