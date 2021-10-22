## OpenShift GitOps ##

#### Deployment Steps ####

1. ```oc apply -k gitops```

2. ```oc apply -f subscription/argocd.yaml```

3. ```oc apply -f instance/argocd.yaml```

#### Folder Overview ####

```gitops```
Installs the OpenShift GitOps operator

```subscription```
Subscribes to the operators

```instance```
Provisions instances within the operators. For example, MultiClusterHub for RHACM