# 🛠️ DevOps Tools Installation Guide

A comprehensive, copy-paste-ready reference for installing essential DevOps tools on **Amazon EC2 (Ubuntu)** instances.

> Each guide includes prerequisites, step-by-step installation commands, verification steps, common commands, and uninstall instructions.

---

## 📋 Table of Contents (Install in this order ⬇️)

| # | Tool | Requires | Description |
|---|------|----------|-------------|
| 1 | [Docker](guides/docker.md) | — | Container runtime (install this first!) |
| 2 | [Docker Compose](guides/docker-compose.md) | Docker | Run multi-container applications |
| 3 | [Kubernetes](guides/kubernetes.md) | Docker | kubectl, Minikube & Kind |
| 4 | [Helm](guides/helm.md) | kubectl + Cluster | Kubernetes package manager |
| 5 | [ArgoCD](guides/argocd.md) | kubectl + Cluster | GitOps continuous delivery |
| 6 | [Terraform](guides/terraform.md) | — | Infrastructure as Code |
| 7 | [Ansible](guides/ansible.md) | — | Configuration management & automation |
| 8 | [Prometheus](guides/prometheus.md) | — | Metrics collection & alerting |
| 9 | [Grafana](guides/grafana.md) | Prometheus (optional) | Monitoring & observability dashboards |
| 10 | [Jenkins](guides/jenkins.md) | — | CI/CD automation server |
| 11 | [Nginx](guides/nginx.md) | — | Web server & reverse proxy |
| 12 | [SonarQube](guides/sonarqube.md) | Docker | Code quality & security analysis |
| 13 | [Trivy](guides/trivy.md) | — | Container & image vulnerability scanner |

---

## 🚀 How to Use

1. Launch an **Amazon EC2** instance (Ubuntu 22.04+ recommended)
2. SSH into the instance
3. Open the guide for the tool you need
4. Copy and paste the commands directly into your terminal

---

## 📌 EC2 Quick Setup Reminder

```bash
# Update the system first (always do this on a fresh EC2)
sudo apt update && sudo apt upgrade -y

# Install common prerequisites
sudo apt install -y curl wget git unzip software-properties-common apt-transport-https ca-certificates gnupg lsb-release
```

---

## 🔗 Resources

- [AWS EC2 Documentation](https://docs.aws.amazon.com/ec2/)
- [Ubuntu Server Guide](https://ubuntu.com/server/docs)

---

## 📄 License

This project is open source and available for personal reference and learning.
