## Application

```yaml

apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: connectivity-test
  namespace: openshift-gitops
spec:
  project: default
  source:
    repoURL: https://github.com/svghadi/argocd-reproducer.git
    targetRevision: label-mismatch
    path: ./
  destination:
    server: https://kubernetes.default.svc
    namespace: openshift-gitops
  syncPolicy:
    automated:
      prune: true
      selfHeal: false
```

## Fix

Change the backend Service selector from: 

```
selector:
  app: backend-v2
```
To:
```
selector:
  app: backend
```
