# ArgoCD-deploy
Wrapper helm chart repo for ArgoCD

## Quick Start

ArgoCD should be deployed already as a child of control-plane parent app


Access ArgoCD web GUI (pre-networking)
```
Get Password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath='{.data.password}' | base64 -d; echo

Default URL
argocd.lab
```
