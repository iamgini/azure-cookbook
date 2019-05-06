# Azure CLI Cheatsheet
**Powershell and Azure CLI**

## Get Details
```
Get-AzureRmVM -Name VM_NAME -ResourceGroupName RG_NAME
                                    # Get details of a VirtualMachine           
Get-AzureRmVMUsage -Location UKSouth                                    
                                    # Get VM Quota Details of location. 
                                    # Remember to set subscription via AzContext
```

## Troubleshooting
```
Get-AzureRMLog -CorrelationId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -DetailedOutput
                                    # Get log detrails
```

## Formatting output
```
> Get-AzureRmVMUsage -Location UKSouth | Where-Object {$_.Limit -eq 25000}
> Get-AzureRmVMUsage -Location UKSouth | Where-Object {$_.Name.Value -like "*FS*"}
Name                       Current Value Limit  Unit
----                       ------------- -----  ----
Standard FS Family vCPUs             496   500 Count
Standard FSv2 Family vCPUs             0   350 Count

```
