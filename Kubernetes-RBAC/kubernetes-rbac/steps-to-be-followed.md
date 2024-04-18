# Create Role and RoleBinding for any test user

```
vim role-rolebinding.yaml

---
apiVersion: v1
kind: Namespace
metadata:
  name: demo
---
apiVersion: rbac.authorization.k8s.io/v1
kind: Role
metadata:
  name: reader
  namespace: demo
rules:
- apiGroups: [""]
  resources: ["pods", "services"]
  verbs: ["get", "watch", "list"]
- apiGroups: ["apps"]
  resources: ["deployments"]
  verbs: ["get", "watch", "list"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  name: reader-binding
  namespace: demo
subjects:
- kind: Group
  name: reader
  apiGroup: rbac.authorization.k8s.io
roleRef:
  kind: Role
  name: reader
  apiGroup: rbac.authorization.k8s.io
```
```
kubectl apply -f role-rolebinding.yaml
kubectl get roles -n demo
kubectl get rolebindings -n demo
```

**Create certificates so that user can access the cluster**

```
mkdir cred && cd cred
openssl genrsa -out johny.key 2048
```

```
CN: This will be set as username
O: Org name. This is actually used as a group by kubernetes while authenticating/authorizing users. You could add as many as you need


openssl req -new -key johny.key -out johny.csr -subj "/CN=johny/O=demo/O=myorganisation.com"
```

**Convert the CSR to Base64**
```
cat johny.csr | base64 | tr -d '\n'
```

**create certificate signing request**

The CSR file after encoding to base64 we need to send to kubernetes and ask kubernetes to register it. Finally we need to approve this request.
```
cat csr-johny.yaml

kind: CertificateSigningRequest
apiVersion: certificates.k8s.io/v1
metadata:
  name: johny
spec:
  groups:
  - system:authenticated
  request: <paste base64 string from above step>
  signerName: beta.eks.amazonaws.com/app-serving          ###kubernetes.io/kube-apiserver-client
  usages:
  - digital signature
  - key encipherment
  - server auth
```
```
kubectl apply -f csr-johny.yaml
kubectl get csr
```

**Approve certificate signing request**

```
kubectl certificate approve johny
kubectl get csr
```

**create .crt extension certificate file from the token**

```
kubectl get csr johny -o jsonpath='{.status.certificate}' | base64 --decode > johny.crt
```

**configure these details in kubeconfig file**

```
kubectl config set-credentials johny --client-certificate=johny.crt --client-key=johny.key
```

Share this kubeconfig file with user so that user can access the namespace within the cluster

```
kubectl config set-context johny-context --cluster=aks-cluster --user=johny --namespace=demo

kubectl config get-contexts
kubectl config use-context johny-context
```


