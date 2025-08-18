# argocd-deploy
Wrapper helm chart repo for ArgoCD

## Quick start

```bash
# 1) Add upstream repo once
helm repo add argo https://argoproj.github.io/argo-helm
helm repo update

# 2) From this directory, pull chart deps
helm dependency update .

# 3) Install into the 'argocd' namespace
helm upgrade --install argocd . -n argocd --create-namespace

# 4) Get the initial admin password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

## Tweaks

If you prefer Ingress instead of LoadBalancer, set:
```yaml
argocd:
server:
service:
type: ClusterIP
ingress:
enabled: true
ingressClassName: nginx
hosts: [ "argocd.home.lab" ]
```
then upgrade with `-f your-values.yaml`.

Pin the upstream chart version in `Chart.yaml` as needed.