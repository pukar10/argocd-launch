# ArgoCD-deploy
Wrapper helm chart repo for ArgoCD

## Quick Start

Deploy ArgoCD Helm chart
```
helm upgrade -i argocd helm/ \
  -n argocd --create-namespace \
  -f helm/local/values.yaml \
  --dependency-update \
  --wait
```

Access ArgoCD web GUI before deploying networking
```
kubectl -n argocd port-forward svc/argocd-server 8080:80

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d; echo
```

Uninstall ArgoCD Helm chart
```
helm uninstall argocd -n argocd

kubectl delete ns argocd
```
