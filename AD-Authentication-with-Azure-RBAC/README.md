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








**Refernce**=https://github.com/MicrosoftDocs/azure-docs/blob/main/articles/role-based-access-control/built-in-roles/containers.md
