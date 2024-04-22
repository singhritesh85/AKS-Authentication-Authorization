# AKS Azure AD Authentication with AZURE RBAC

**In this kind of Azure AKS Authentication and Authorization, Authentication of user will be done using Azure AD and it's Authorization will be done using Azure Role Based Access Control (Azure RBAC).**
<br><br/>
I have demonstrated this with the help of creation of two Azure AD users named as demo-user and admin-user in the Azure AD groups demo-group and admin-group respectively. The demo-user have only the Read access for pods, services and deployments. While the admin-user have admin access.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/e91c8c4b-eaa4-4b1d-832e-4a548cc71c56)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/88b3a86d-e759-41e7-b402-15d98c6e1cac)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/d8bd7309-5f0b-4158-a511-4adf8d93c9a3)

<br><br/>
From the Azure Console cluster configuration tab the Authentication and Authorization option is changed to **Azure AD authentication with Azure RBAC**.
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/385ff2b2-1ab7-4268-a3a7-934ffe91b348)
Create 
```
(a) Create a Custom Role to get Read Access for Pods, Services and Deployments (When you create a Custom Role in Azure the Assignable scopes can be ManagementGroup, Subscription or ResourceGroup).
(b) Assign this Azure Role to Azure AKS (You can assign an Azure Role to User, Group, Service Principle or Managed Identity for the scope of Azure Resource).
```
<br><br/>
Here I have assigned this Azure Role to Azure AD Group for the Scope as Azure Resource AKS. 
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/e4cc1019-45e2-4870-ae1c-4603a1e9fada)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/859fe817-5863-48de-81bd-bb511cde54b5)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/ab0df7dd-2df1-4f35-ba9b-fc594b8d6900)
<br><br/>
```
az role assignment create --role <Name_of_the_Azure_Role as mentioned in the Azure Role definition> --assignee <Object_ID of Group> --scope <Resource_ID of Azure Resource which you can get from Properties tab of Azure Resource>
```
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/7788cdad-16e9-4233-996f-decb5fe2d1e1)
<br><br/>
To generate kubeconfig file Azure Role **Azure Kubernetes Service Cluster User Role** was assigned to Azure AD Group demo-group for Azure AKS cluster named as aks-cluster 
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/18ae1bee-b6ec-48cb-9161-a220459e420b)
<br><br/>
As per the Azure Role the demo-user is only authorize for Read access of Pods, Services and Deployments in namespace demo which can be verified with the screenshots attached below.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/1fb95ef6-8b78-4853-b994-a853d3e15cb8)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/59708a4f-ec85-48f1-b7c6-02a87d574362)

<br> <br/>
**Reference**=https://github.com/MicrosoftDocs/azure-docs/blob/main/articles/role-based-access-control/built-in-roles/containers.md
