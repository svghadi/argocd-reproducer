## Application

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Application
metadata:
  name: oom-test
  namespace: openshift-gitops
spec:
  destination:
    namespace: openshift-gitops
    server: 'https://kubernetes.default.svc'
  project: default
  source:
    path: ./
    repoURL: 'https://github.com/svghadi/argocd-reproducer.git'
    targetRevision: oom
  syncPolicy:
    automated:
      enabled: true
      prune: false
      selfHeal: false
```

## Resources Update

```yaml
resources:
  requests:
    memory: 128Mi
    cpu: 10m
  limits:
    memory: 256Mi
    cpu: 100m
```
