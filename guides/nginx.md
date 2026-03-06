# 🌐 Nginx

> Default port: **80** (HTTP), **443** (HTTPS) — open in EC2 Security Group

## Install

```bash
sudo apt update
sudo apt install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
```

Access: `http://<EC2_PUBLIC_IP>` → You should see "Welcome to nginx!"

## Verify

```bash
sudo systemctl status nginx
nginx -v
sudo nginx -t                          # Test config syntax
```

## Common Commands

```bash
sudo systemctl start/stop/restart nginx
sudo systemctl reload nginx            # Reload without downtime
sudo tail -f /var/log/nginx/error.log
sudo tail -f /var/log/nginx/access.log
sudo nginx -t                          # Validate config
```

## Important Paths

```
/etc/nginx/nginx.conf                  # Main config
/etc/nginx/sites-available/            # Available sites
/etc/nginx/sites-enabled/              # Enabled sites
/var/www/html/                         # Default web root
```

## Reverse Proxy Example

```bash
sudo nano /etc/nginx/sites-available/myapp
```
```nginx
server {
    listen 80;
    server_name yourdomain.com;
    location / {
        proxy_pass http://localhost:3000;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
    }
}
```
```bash
sudo ln -s /etc/nginx/sites-available/myapp /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
```

## SSL with Certbot

```bash
sudo apt install -y certbot python3-certbot-nginx
sudo certbot --nginx -d yourdomain.com
sudo certbot renew --dry-run            # Test auto-renewal
```

## Uninstall

```bash
sudo apt purge -y nginx nginx-common
sudo rm -rf /etc/nginx
```
