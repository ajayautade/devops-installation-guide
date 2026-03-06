# 🔥 Prometheus

> Default port: **9090** (Prometheus), **9100** (Node Exporter) — open in EC2 Security Group

## Install Prometheus

```bash
# Create user and directories
sudo useradd --no-create-home --shell /bin/false prometheus
sudo mkdir -p /etc/prometheus /var/lib/prometheus

# Download (check latest version at https://prometheus.io/download/)
cd /tmp
wget https://github.com/prometheus/prometheus/releases/download/v2.53.0/prometheus-2.53.0.linux-amd64.tar.gz
tar xvfz prometheus-2.53.0.linux-amd64.tar.gz
cd prometheus-2.53.0.linux-amd64

# Install
sudo cp prometheus promtool /usr/local/bin/
sudo cp -r consoles console_libraries prometheus.yml /etc/prometheus/
sudo chown -R prometheus:prometheus /etc/prometheus /var/lib/prometheus /usr/local/bin/prometheus /usr/local/bin/promtool
```

## Create Systemd Service

```bash
sudo tee /etc/systemd/system/prometheus.service > /dev/null <<EOF
[Unit]
Description=Prometheus
After=network-online.target

[Service]
User=prometheus
Group=prometheus
Type=simple
ExecStart=/usr/local/bin/prometheus \
  --config.file /etc/prometheus/prometheus.yml \
  --storage.tsdb.path /var/lib/prometheus/

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl start prometheus
sudo systemctl enable prometheus
```

## Install Node Exporter

```bash
sudo useradd --no-create-home --shell /bin/false node_exporter
cd /tmp
wget https://github.com/prometheus/node_exporter/releases/download/v1.8.2/node_exporter-1.8.2.linux-amd64.tar.gz
tar xvfz node_exporter-1.8.2.linux-amd64.tar.gz
sudo cp node_exporter-1.8.2.linux-amd64/node_exporter /usr/local/bin/
sudo chown node_exporter:node_exporter /usr/local/bin/node_exporter

sudo tee /etc/systemd/system/node_exporter.service > /dev/null <<EOF
[Unit]
Description=Node Exporter
After=network-online.target

[Service]
User=node_exporter
Group=node_exporter
Type=simple
ExecStart=/usr/local/bin/node_exporter

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl start node_exporter
sudo systemctl enable node_exporter
```

Then add to `/etc/prometheus/prometheus.yml` under `scrape_configs`:
```yaml
  - job_name: 'node_exporter'
    static_configs:
      - targets: ['localhost:9100']
```
```bash
sudo systemctl restart prometheus
```

## Verify

```bash
sudo systemctl status prometheus
sudo systemctl status node_exporter
# UI: http://<EC2_PUBLIC_IP>:9090
# Targets: http://<EC2_PUBLIC_IP>:9090/targets
```

## Common Commands

```bash
sudo systemctl start/stop/restart prometheus
sudo systemctl start/stop/restart node_exporter
sudo journalctl -u prometheus -f       # Prometheus logs
promtool check config /etc/prometheus/prometheus.yml  # Validate config
```

## Uninstall

```bash
sudo systemctl stop prometheus node_exporter
sudo systemctl disable prometheus node_exporter
sudo rm /etc/systemd/system/prometheus.service /etc/systemd/system/node_exporter.service
sudo rm /usr/local/bin/prometheus /usr/local/bin/promtool /usr/local/bin/node_exporter
sudo rm -rf /etc/prometheus /var/lib/prometheus
sudo userdel prometheus && sudo userdel node_exporter
sudo systemctl daemon-reload
```
