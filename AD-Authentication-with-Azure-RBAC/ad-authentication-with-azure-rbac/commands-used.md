1. az role definition create --role-definition authorization.json
2. az role assignment create --role "AKS Pod Service Deployment Read Access" --assignee ceeXXXXX-1XXf-4XX0-aXXa-4beXXXXXXdc0 --scope /
subscriptions/512XXXX6-aXX4-4XX6-9XX4-f1XXXXXX15d/resourcegroups/aks-rg/providers/Microsoft.ContainerService/managedClusters/aks-cluster/namespaces/demo



**Reference** 
```
https://learn.microsoft.com/en-us/azure/role-based-access-control/tutorial-custom-role-cli
https://learn.microsoft.com/en-us/azure/role-based-access-control/custom-roles-cli
https://learn.microsoft.com/en-us/answers/questions/1082464/namespace-permission
https://github.com/MicrosoftDocs/azure-docs/blob/main/articles/role-based-access-control/built-in-roles/containers.md
```
