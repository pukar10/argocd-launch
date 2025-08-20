# ArgoCD-deploy
Wrapper helm chart repo for ArgoCD

## Quick Start

```
helm upgrade -i argocd argocd-deploy/charts/argocd-deploy \
  -n argocd --create-namespace \
  -f argocd-deploy/local/values-homelab.yaml \
  --dependency-update
  --wait
```
