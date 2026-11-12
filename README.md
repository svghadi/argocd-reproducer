## Application

```yaml

apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: db
  namespace: openshift-gitops
spec:
  project: default
  source:
    repoURL: https://github.com/svghadi/argocd-reproducer.git
    targetRevision: HEAD
    path: missing-configmap
  destination:
    server: https://kubernetes.default.svc
    namespace: openshift-gitops
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
```


## Missing configmap

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
  namespace: gitops-ai-test
data:
  database-host: "postgres.gitops-ai-test.svc.cluster.local"
```
