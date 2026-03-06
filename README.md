# 🛠️ DevOps Tools Installation Guide

A comprehensive, copy-paste-ready reference for installing essential DevOps tools on **Amazon EC2 (Ubuntu)** instances.

> Each guide includes prerequisites, step-by-step installation commands, verification steps, common commands, and uninstall instructions.

---

## 📋 Table of Contents

| # | Tool | Description |
|---|------|-------------|
| 1 | [Docker](guides/docker.md) | Container runtime & Docker Compose |
| 2 | [Kubernetes](guides/kubernetes.md) | kubectl, Minikube & Kind |
| 3 | [ArgoCD](guides/argocd.md) | GitOps continuous delivery for Kubernetes |
| 4 | [Grafana](guides/grafana.md) | Monitoring & observability dashboards |
| 5 | [Prometheus](guides/prometheus.md) | Metrics collection & alerting |
| 6 | [Jenkins](guides/jenkins.md) | CI/CD automation server |
| 7 | [Terraform](guides/terraform.md) | Infrastructure as Code |
| 8 | [Ansible](guides/ansible.md) | Configuration management & automation |
| 9 | [Helm](guides/helm.md) | Kubernetes package manager |
| 10 | [Nginx](guides/nginx.md) | Web server & reverse proxy |
| 11 | [SonarQube](guides/sonarqube.md) | Code quality & security analysis |
| 12 | [Trivy](guides/trivy.md) | Container & image vulnerability scanner |

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
