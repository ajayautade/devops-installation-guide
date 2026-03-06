# ☸️ Kubernetes (kubectl, Minikube, Kind)

## kubectl

```bash
curl -LO "https://dl.k8s.io/release/$(curl -Ls https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
rm kubectl
kubectl version --client
```

## Minikube

> Requires Docker installed first

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
rm minikube-linux-amd64

# Start cluster
minikube start --driver=docker
```

## Kind

> Requires Docker installed first

```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.25.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind

# Create cluster
kind create cluster --name my-cluster
```

## Common Commands

```bash
kubectl get nodes                      # List nodes
kubectl get pods -A                    # All pods
kubectl get svc                        # Services
kubectl apply -f <file.yaml>           # Apply manifest
kubectl delete -f <file.yaml>          # Delete resources
kubectl describe pod <name>            # Pod details
kubectl logs <pod>                     # Pod logs
kubectl exec -it <pod> -- bash         # Shell into pod
kubectl config get-contexts            # List contexts
kubectl config use-context <name>      # Switch context
minikube start / stop / delete         # Minikube lifecycle
kind create cluster / delete cluster   # Kind lifecycle
```

## Uninstall

```bash
sudo rm /usr/local/bin/kubectl
minikube delete --all && sudo rm /usr/local/bin/minikube
kind delete cluster --name my-cluster && sudo rm /usr/local/bin/kind
```
