
#### WORK IN PROGRESS ####

1. Login to the OpenShift Cluster via the CLI

2. Install GitOps Operator
    ```oc apply -f cluster-config/gitops-operator/namespace.yaml```
    ```oc apply -f cluster-config/gitops-operator/operator-group.yaml```
    ```oc apply -f cluster-config/gitops-operator/subscription.yaml```

3. Give ArgoCD permission to create resources
    ```oc adm policy add-scc-to-user anyuid system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller```
    ```oc adm policy add-cluster-role-to-user cluster-admin system:serviceaccount:openshift-gitops:openshift-gitops-argocd-application-controller```

4. Login to the ArgoCD cluster
    ```oc get route openshift-gitops-server -n openshift-gitops```
    ```argocd login <route from above>```
    Username: admin
    Password: ```oc get secret openshift-gitops-cluster -n openshift-gitops -ojsonpath='{.data.admin\.password}' | base64 -d```    

5. Create ArgoCD application set and project
    ```oc apply -f cluster-config/argocd.yaml```


### Viewing the ArgoCD Console ###

1. Navigate to the ArgoCD console
    ```oc get route openshift-gitops-server -n openshift-gitops```

2. Enter credentials in the ArgoCD console
    Username: admin
    Password: ```oc get secret openshift-gitops-cluster -n openshift-gitops -ojsonpath='{.data.admin\.password}' | base64 -d```