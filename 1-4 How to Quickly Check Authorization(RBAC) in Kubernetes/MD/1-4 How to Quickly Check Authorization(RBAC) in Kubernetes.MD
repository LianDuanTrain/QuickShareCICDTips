# How to Quickly Check Authorization(RBAC) in Kubernetes? 

## Video Topics  
- Demo ENV Detail    
- Quickly Check Authorization(RBAC) in Kubernetes
  

## Demo ENV Detail

- OS version - Oracle Linux Server release 8.4   
  - `cat /etc/oracle-release`
- Minikube and Kubernetes Version   
  <img src="images/version.jpg" width="80%">
- Related Videos  
  - [Kubernetes Security Role Based Access Control](https://youtu.be/r05cPdoLoLw)   
  - [How to Install Elasticsearch, Kibana,Logstash, Filebeat and Java App on Minikube](https://youtu.be/vN0BrVvmUxc)

  
## Quickly Check Authorization(RBAC) in Kubernetes

- Check RBAC via Command Line  
  - ' kubectl auth can-i '
    -  User
    -  ServiceAccount
- Check RBAC via Resource 
  - SelfSubjectAccessReview   
-  https://kubernetes.io/docs/reference/access-authn-authz/authorization/#determine-the-request-verb   
-  <img src="images/verbs.jpg" width="80%">   
  
  
###  Hands On Demo

#### Create ClusterRole, ServiceAccount, and RoleBinding   
```  
apiVersion: v1
kind: Namespace
metadata:
  name: elk
---    
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  namespace: elk
  name: filebeat
  labels:
    app: filebeat
rules:
- apiGroups: [""]
  resources:
  - namespaces
  - pods
  - nodes
  verbs:
  # https://kubernetes.io/docs/reference/access-authn-authz/authorization/#determine-the-request-verb
  - get
  - watch
  - list
---
apiVersion: v1
kind: ServiceAccount
metadata:
  namespace: elk
  name: filebeat
  labels:
    app: filebeat
---
apiVersion: rbac.authorization.k8s.io/v1
kind: RoleBinding
metadata:
  namespace: elk
  name: filebeat
subjects:
- kind: ServiceAccount
  name: filebeat
  namespace: elk
roleRef:
  kind: ClusterRole
  name: filebeat
  apiGroup: rbac.authorization.k8s.io
---

``` 
- `kubectl apply -f filebeat-role-v1.yaml`

####  Authorization Verification

- Command Line   
  - `kubectl auth can-i list pods --namespace elk --as system:serviceaccount:elk:filebeat`   
  - `kubectl auth can-i create pods --namespace elk --as system:serviceaccount:elk:filebeat`   
  - `kubectl auth can-i list pods --namespace default --as system:serviceaccount:default:filebeat` 
  - https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#auth  
- Create a resource 
```    
kubectl create -f  - --as system:serviceaccount:elk:filebeat -o yaml << EOF
apiVersion: authorization.k8s.io/v1
kind: SelfSubjectAccessReview
spec:
    resourceAttributes:
        group: "*"
        name: deployments
        verb: create
        namespace: elk
EOF
  ```    
- Clear Up  
   - `kubectl delete -f filebeat-role-v1.yaml`   








