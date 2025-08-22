# ArgoCD-deploy
Wrapper helm chart repo for ArgoCD

## Quick Start

Deploy ArgoCD (Helm managed)
```
helm upgrade -i argocd helm/ \
  -n argocd --create-namespace \
  -f helm/local/values.yaml \
  --dependency-update \
  --wait
```

Deploy ArgoCD (not managed by Helm)
```
helm dependency update helm/
helm template argocd helm/ \
  --include-crds \
  -n argocd \
  -f helm/local/values.yaml \
  | kubectl apply -n argocd --create-namespace -f -
```

Access ArgoCD web GUI (pre-networking)
```
Get Password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d; echo

Port forward svc
kubectl -n argocd port-forward svc/argocd-server 8080:80

Port forward directly
kubectl -n argocd port-forward deploy/argocd-server 8080:8080
```

Uninstall ArgoCD
```
helm uninstall argocd -n argocd

kubectl delete ns argocd
```
