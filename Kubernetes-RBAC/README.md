# Kubernetes RBAC in AKS
To demonstrate Kubernetes RBAC in AKS I have created two users one is named as johny who got the get, watch and list authorization for pods, services and deployments (defined using Role) and another is named as prabhakar who has cluster administrator authorization (defined using ClusterRole).
<br><br/>
Role and RoleBinding
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/072a4ffd-21ae-4b2d-802f-65b4a8f5e359)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/7ef92f5a-6cdb-4a1d-8cbf-352571922e41)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/76f622a8-cb45-4c9c-8b44-28bd554ac121)
<br><br/>
ClusterRole and ClusterRoleBinding
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/7f0946bf-43c6-4ecc-a684-4fce022f569f)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/f574c6c3-708b-43c6-b234-3492a35d0b14)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/5b21259a-2644-4ce3-a0b1-22345eb72659)
<br><br/>
Create a directory to keep the certificates and key for johny user, generate the certificates and key
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/1b019d52-a0e9-427b-a19a-3703f70d013b)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/1918c3d9-5516-434a-9df7-a8300866a439)
<br><br/>
convert CSR to base64
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/45fb8b22-7bdd-45e8-848b-826abf76373f)
<br><br/>
create certificate signing request
```
The CSR file after encoding to base64 we need to send to AKS and ask AKS to register it. Finally we need to approve this request.
```
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/15d418d0-de3a-4a3d-8bc3-864b850994db)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/863394b7-1fe2-47a5-a760-82f18e62ad3d)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/135c14cd-bccd-4537-8375-626b3d326527)
<br><br/>
create .crt extension certificate file from the token
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/e854a4f8-5ca6-46bb-a626-690e6dba19df)
<br><br/>
configure these details in kubeconfig file
<br><>br/
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/4425ad30-c551-4420-86bb-64f4e4bcccdd)
<br><br/>
create user context
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/00da6f51-c634-444b-b5c9-5349c99d37bc)
list user context
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/6540d0d5-a4a6-42f9-b8a2-24ff39d407e0)
switch context
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/e46f8aa4-cc80-4dcf-b16f-b554359673f7)
You can share these kubeconfig file and certificate files (johny.key and johny.crt files) with user johny as shown in screenshot below so that user johny can access the AKS cluster namespace demo with limited access of list, watch and get the pods, services and deployments.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/159631d8-74a6-4709-8b55-6d0e08ccd797)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/671221f3-b051-47e6-9447-708abc07ca44)
<br> <br/>
The same steps have been followed for user prabhakar who has admin access.
<br><br/>
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/90de5210-51fb-466b-a8dc-80a9533e84aa)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/b3efa592-afc5-4c98-83fb-845906b30e99)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/76587e03-7132-44c5-a6a8-95eed3eba4b7)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/119b9a0f-888d-4f5a-89d2-ab94f779ff47)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/ad0db008-9677-4eff-9332-4f91919de282)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/19217040-60df-4828-b8bf-c94eb3fa589e)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/5b3752de-7965-49da-9a09-93cf8986e3a3)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/a6032a27-6c00-44e9-b39e-bcc8d10e3fb6)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/b87ba5ef-52c8-4491-b838-cb731642444e)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/1227ad91-ff69-4579-8469-72197480eb2b)

Share the kubeconfig file, prabhakar.crt and prabhakar.key with user prabhakar after which user will be able to access the kubernetes cluster.
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/927ac6da-7072-437b-9897-f0ad457cb639)
![image](https://github.com/singhritesh85/AKS-Authentication-Authorization/assets/56765895/2e1ca319-9cc8-447d-a304-ce6b4cb7c68d)
