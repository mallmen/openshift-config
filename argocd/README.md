Apply the manifest to install the operator and create the initial ArgoCD instance:

` oc apply -f gitops-install.yaml`

Wait for the operator and ArgoCD instance to finish deploying, then grant cluster-admin access to apply configuration using ArgoCD:

`oc apply -f gitops-role.yaml`

Get the default admin password:

`oc get secret openshift-gitops-cluster -n openshift-gitops -o jsonpath='{.data.admin\.password}' | base64 -d^`

Get the ArgoCD route:

`oc get route openshift-gitops-server -n openshift-gitops`

Create the App of Apps configuration:

`oc apply -f app-of-apps.yaml`
