# rejekts-eu-2023-gitops
GitOps repo for demo. For more information check [https://github.com/salaboy/rejekts-eu-2023/](https://github.com/salaboy/rejekts-eu-2023/)

This repo is being synced by ArgoCD and using this resource: 

```
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: production-environment
spec:
  destination:
    name: in-cluster
    namespace: production
    server: ''
  source:
    path: production
    repoURL: 'https://github.com/salaboy/rejekts-eu-2023-gitops'
    targetRevision: HEAD
  project: default
```

The target Cluster needs to have Knative Serving and Dapr installed as well as a Redis Instance, that you can install by running: 

```
helm repo add bitnami https://charts.bitnami.com/bitnami
helm install redis bitnami/redis --set architecture=standalone
```