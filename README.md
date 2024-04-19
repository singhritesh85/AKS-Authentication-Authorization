# AKS-Authentication-Authorization

```
There are mainly three Access and Identity Options with AKS
(a) Local Accounts with Kubernetes RBAC
(b) Azure AD authentication with Kubernetes RBAC
(c) Azure AD authentication with Azure RBAC 
```
To demonstrate three types of Accesses I have created the AKS cluster using the terraform script present in my GitHub Repo https://github.com/singhritesh85/terraform-azure and inside the directory azure-aks-withoutmanagedprometheusgrafana
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/c9b0fd50-af67-4700-8d5e-0aace3a03ace)
<br><br/>
**Difference between Role and cluster-Role is Role is used to provide privileges in one namespace while Cluster-Role is used to provide privileges over all the namespaces within the cluster.**
<br><br/>
**Difference between RoleBinding and ClusterRoleBinding is RoleBinding is used to bind Role with a User or Group and ClusterRoleBinding is used to bind ClusterRole with a User or Group.**
