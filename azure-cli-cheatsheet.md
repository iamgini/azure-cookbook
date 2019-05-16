# Azure CLI Cheatsheet
**Powershell and Azure CLI**

## Set Azure Subscription and Tenant
You need to set this before executing commands if you have multiple subscriptions and tenant ID.
```
Select-AzureRmSubscription -TenantId TENANT_ID -SubscriptionId SUBSCRIPTION_ID
```

## Get Details
```
Get-AzureRmVM -Name VM_NAME -ResourceGroupName RG_NAME
                                    # Get details of a VirtualMachine           
Get-AzureRmVMUsage -Location UKSouth                                    
                                    # Get VM Quota Details of location. 
                                    # Remember to set subscription via AzContext
```
# Get details, Filter Out and Select Fields to Display
1)
```
Get-AzureRmNetworkSecurityGroup -Name NETWORK_SECURITY_GROUP -ResourceGroupName RESOURCE_GROUP |Get-AzureRmNetworkSecurityRuleConfig
                                    # Get rules in Network Security Groups 
```
2)
```
Get-AzureRmNetworkSecurityGroup -Name NETWORK_SECURITY_GROUP -ResourceGroupName RESOURCE_GROUP |Get-AzureRmNetworkSecurityRuleConfig |? DestinationPortRange -eq 3306   
                                    # Get rules in Network Security Groups 
                                    # and Filter with Port
```
3)
```
Get-AzureRmNetworkSecurityGroup -Name NETWORK_SECURITY_GROUP -ResourceGroupName RESOURCE_GROUP |Get-AzureRmNetworkSecurityRuleConfig |? DestinationPortRange -eq 3306 |select Name,DestinationPortRange,SourceAddressPrefix,DestinationAddressPrefix    
                                    # Get rules in Network Security Groups 
                                    # and Filter with Port
                                    # and show only required fields
```

## Troubleshooting
```
Get-AzureRMLog -CorrelationId xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx -DetailedOutput
                                    # Get log detrails
```

## Formatting output
```
> Get-AzureRmVMUsage -Location UKSouth | Where-Object {$_.Limit -eq 25000}
> Get-AzureRmVMUsage -Location UKSouth | ? Limit -eq 2000
> Get-AzureRmVMUsage -Location UKSouth | Where-Object {$_.Name.Value -like "*FS*"}
Name                       Current Value Limit  Unit
----                       ------------- -----  ----
Standard FS Family vCPUs             496   500 Count
Standard FSv2 Family vCPUs             0   350 Count

```
