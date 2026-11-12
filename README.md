# argocd-reproducer
Examples to reproduce Argo CD bugs

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
