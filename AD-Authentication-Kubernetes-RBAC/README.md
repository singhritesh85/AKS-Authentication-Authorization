# Azure AD authentication with Kubernetes RBAC

**In this kind of Azure AKS Authentication and Authorization the Authentication of user will be done using Azure AD and it's Authorization will be done using Kubernetes Role Based Access Control(Role, RoleBinding, ClusterRole and ClusterRoleBinding).**

To demonstrate this I have created two Azure AD users demo-user and admin-user within the Azure AD groups demo-group and admin-group respectively.
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/abac96bc-9f97-4abe-887d-336ae6ff7e9b)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/e8a9cabb-2a08-43c1-9ed5-ba85c3dbb2b5)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/0b896a8f-d201-47ea-ab5f-07feeb3a68dc)
<br><br/>
From the Azure Console cluster configuration tab the Authentication and Authorization option is changed to **Azure AD authentication with Kubernetes RBAC** and for **Cluster admin ClusterRoleBinding** option an Azure AD Group should be attached. The **Users within this Azure AD group will get admin access within the cluster**.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/c453443d-b027-448e-bcc7-d2481232025e)
<br><br/>
The demo-user is authorized using the Role and RoleBinding as shown in the screenshot attached below. Demo-User can perform get, watch and list operations on Pod, Services and Deployment within the namespace demo. In the Subject of RoleBinding I have used **Object ID** of the Azure AD Group and the namespace which indicates the User within this Azure AD Group will have Authorization as mentioned in the Role which will be bind using the RoleBinding.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/816b2242-6fc2-4c9d-92dd-4a091345b092)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/a3e8c977-dc0c-45ac-aded-79918b259738)
<br><br/>
Provide **Azure Kubernetes Service Cluster User Role** to the two Azure AD Groups demo-group and admin-group. As this Role is needed to generate the kubeconfig file. 
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/bf406654-7cdb-40b6-aa83-1ff4cd298a2a)
