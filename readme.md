## OpenShift GitOps ##

#### Deployment Steps ####

1. ```oc apply -k gitops```

2. ```oc adm policy add-cluster-role-to-user cluster-admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller```

3. ```oc apply -f subscription/argocd.yaml```

4. ```oc apply -f instance/argocd.yaml```

#### Folder Overview ####

```gitops```
- Installs the OpenShift GitOps operator

```subscription```
- Subscribes to the operators
    - argocd.yaml creates the ArgoCD app 
    - module-set.yaml creates the ArgoCD application set, calling the operator folders
    - operators folder contains the yamls for operator subscription

```instance```
- Provisions instances within the operators. For example, MultiClusterHub for RHACM
    - argocd.yaml creates the ArgoCD app 
    - module-set.yaml creates the ArgoCD application set, calling the operator folders
    - operators folder contains the yamls to provision instances of operators