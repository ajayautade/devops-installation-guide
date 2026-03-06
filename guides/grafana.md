# 📊 Grafana

> Default port: **3000** — open in EC2 Security Group

## Install

```bash
sudo apt install -y apt-transport-https software-properties-common wget

# Add repo
sudo mkdir -p /etc/apt/keyrings/
wget -q -O - https://apt.grafana.com/gpg.key | gpg --dearmor | sudo tee /etc/apt/keyrings/grafana.gpg > /dev/null
echo "deb [signed-by=/etc/apt/keyrings/grafana.gpg] https://apt.grafana.com stable main" | sudo tee /etc/apt/sources.list.d/grafana.list

# Install & start
sudo apt update
sudo apt install -y grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server
```

## Access

- URL: `http://<EC2_PUBLIC_IP>:3000`
- Username: `admin` | Password: `admin` (change on first login)

## Verify

```bash
sudo systemctl status grafana-server
```

## Common Commands

```bash
sudo systemctl start grafana-server
sudo systemctl stop grafana-server
sudo systemctl restart grafana-server
sudo journalctl -u grafana-server -f   # View logs
# Config: /etc/grafana/grafana.ini
```

## Add Prometheus Data Source

Go to **Configuration → Data Sources → Add → Prometheus** → URL: `http://localhost:9090` → **Save & Test**

## Uninstall

```bash
sudo systemctl stop grafana-server
sudo apt purge -y grafana
sudo rm -rf /etc/grafana /var/lib/grafana /var/log/grafana
sudo rm /etc/apt/sources.list.d/grafana.list
```
