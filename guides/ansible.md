# ⚙️ Ansible

## Install

```bash
sudo apt update
sudo apt install -y software-properties-common
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install -y ansible
```

## Verify

```bash
ansible --version
ansible localhost -m ping
```

## Common Commands

```bash
# Ad-hoc
ansible all -m ping                    # Ping all hosts
ansible all -a "uname -a"             # Run command on all hosts

# Playbooks
ansible-playbook playbook.yml
ansible-playbook -i inventory.ini playbook.yml
ansible-playbook playbook.yml --check  # Dry run
ansible-playbook playbook.yml -e "var=value"

# Roles
ansible-galaxy init <role_name>
ansible-galaxy install <role_name>

# Vault
ansible-vault create secrets.yml
ansible-vault edit secrets.yml
ansible-playbook playbook.yml --ask-vault-pass

# Inventory: /etc/ansible/hosts
# Config: /etc/ansible/ansible.cfg
```

## Uninstall

```bash
sudo apt purge -y ansible
sudo add-apt-repository --remove ppa:ansible/ansible
```
