# ArgoCD-deploy
Wrapper helm chart repo for ArgoCD

## Quick Start

```
helm upgrade -i argocd helm/ \
  -n argocd --create-namespace \
  -f helm/local/values.yml \
  --dependency-update
  --wait

helm uninstall argocd -n argocd

```
