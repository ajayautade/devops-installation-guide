# 🔄 ArgoCD

> Requires a running Kubernetes cluster + kubectl

## Install

```bash
# Create namespace and install
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# Wait for pods to be ready
kubectl get pods -n argocd -w
```

## Install ArgoCD CLI

```bash
curl -sSL -o argocd https://github.com/argoproj/argo-cd/releases/latest/download/argocd-linux-amd64
sudo install -m 555 argocd /usr/local/bin/argocd
rm argocd
```

## Access the UI

```bash
# Port forward
kubectl port-forward svc/argocd-server -n argocd 8080:443 &

# Get admin password
argocd admin initial-password -n argocd

# Login: https://localhost:8080  |  user: admin
```

## Common Commands

```bash
argocd login localhost:8080 --username admin --password <pass> --insecure
argocd app create <name> --repo <url> --path <path> --dest-server https://kubernetes.default.svc --dest-namespace <ns>
argocd app sync <name>                 # Sync app
argocd app list                        # List apps
argocd app get <name>                  # App details
argocd app delete <name>               # Delete app
argocd account update-password         # Change password
```

## Uninstall

```bash
kubectl delete -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
kubectl delete namespace argocd
sudo rm /usr/local/bin/argocd
```
