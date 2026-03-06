# ⎈ Helm

> Requires kubectl + a running Kubernetes cluster

## Install

```bash
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash
```

## Verify

```bash
helm version
```

## Common Commands

```bash
# Repos
helm repo add <name> <url>             # Add repo
helm repo update                       # Update repos
helm repo list                         # List repos
helm search repo <keyword>             # Search charts

# Install / Manage
helm install <release> <chart>         # Install chart
helm install <release> <chart> -f values.yaml
helm install <release> <chart> --set key=value
helm install <release> <chart> -n <ns> --create-namespace
helm list                              # List releases
helm list -A                           # All namespaces
helm status <release>                  # Release status

# Upgrade / Rollback
helm upgrade <release> <chart>
helm rollback <release> <revision>

# Uninstall
helm uninstall <release>

# Chart dev
helm create <chart_name>               # Create chart skeleton
helm template <release> <chart>        # Render locally
helm lint <chart_dir>                  # Lint chart

# Popular repos
helm repo add bitnami https://charts.bitnami.com/bitnami
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo add grafana https://grafana.github.io/helm-charts
```

## Uninstall

```bash
sudo rm /usr/local/bin/helm
```
