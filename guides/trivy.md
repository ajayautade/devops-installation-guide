# 🛡️ Trivy

## Install

```bash
sudo apt install -y wget gnupg
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | gpg --dearmor | sudo tee /usr/share/keyrings/trivy.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/trivy.gpg] https://aquasecurity.github.io/trivy-repo/deb generic main" | sudo tee /etc/apt/sources.list.d/trivy.list
sudo apt update
sudo apt install -y trivy
```

## Verify

```bash
trivy version
trivy image nginx:latest               # Test scan
```

## Common Commands

```bash
# Image scanning
trivy image <image>                    # Scan Docker image
trivy image --severity HIGH,CRITICAL <image>
trivy image --ignore-unfixed <image>

# Filesystem scanning
trivy fs .                             # Scan current directory
trivy fs /path/to/project

# Git repo scanning
trivy repo https://github.com/<owner>/<repo>

# Kubernetes scanning
trivy k8s --report summary

# Config scanning (Dockerfile, Terraform, K8s manifests)
trivy config .

# CI/CD usage (exit code 1 on findings)
trivy image --exit-code 1 --severity CRITICAL <image>

# Output as JSON
trivy image -f json -o results.json <image>
```

## Uninstall

```bash
sudo apt purge -y trivy
sudo rm /etc/apt/sources.list.d/trivy.list
rm -rf ~/.cache/trivy
```
