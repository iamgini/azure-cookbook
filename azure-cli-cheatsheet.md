# Azure CLI Cheatsheet
Powershell and Azure CLI

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
