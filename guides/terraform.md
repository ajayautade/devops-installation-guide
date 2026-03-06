# 🏗️ Terraform

## Install

```bash
sudo apt update
sudo apt install -y gnupg software-properties-common

# Add HashiCorp repo
wget -O- https://apt.releases.hashicorp.com/gpg | gpg --dearmor | sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

sudo apt update
sudo apt install -y terraform
```

## Verify

```bash
terraform version
```

## Common Commands

```bash
terraform init                         # Initialize project
terraform plan                         # Preview changes
terraform apply                        # Apply changes
terraform apply -auto-approve          # Apply without prompt
terraform destroy                      # Destroy infrastructure
terraform destroy -auto-approve        # Destroy without prompt
terraform fmt                          # Format files
terraform validate                     # Validate config
terraform show                         # Show state
terraform state list                   # List resources
terraform output                       # Show outputs
terraform workspace list/new/select    # Workspace management
```

## Uninstall

```bash
sudo apt purge -y terraform
sudo rm /etc/apt/sources.list.d/hashicorp.list
```
