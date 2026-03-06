# 🔧 Jenkins

> Default port: **8080** — open in EC2 Security Group

## Install

```bash
# Install Java (required)
sudo apt update
sudo apt install -y fontconfig openjdk-17-jre

# Add Jenkins repo
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] https://pkg.jenkins.io/debian-stable binary/" | sudo tee /etc/apt/sources.list.d/jenkins.list > /dev/null

# Install & start
sudo apt update
sudo apt install -y jenkins
sudo systemctl start jenkins
sudo systemctl enable jenkins
```

## Access

```bash
# Get initial admin password
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
```

- URL: `http://<EC2_PUBLIC_IP>:8080`
- Paste the password → Install suggested plugins → Create admin user

## Verify

```bash
sudo systemctl status jenkins
java -version
```

## Common Commands

```bash
sudo systemctl start/stop/restart jenkins
sudo journalctl -u jenkins -f          # View logs
# Home dir: /var/lib/jenkins
# Config: /etc/default/jenkins
```

## Uninstall

```bash
sudo systemctl stop jenkins
sudo apt purge -y jenkins
sudo rm -rf /var/lib/jenkins
```
