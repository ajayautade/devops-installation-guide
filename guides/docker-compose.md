# 🐙 Docker Compose

Docker Compose is a tool for defining and running multi-container Docker applications using a YAML file. 

*(Note: Docker must be installed first. See the [Docker Guide](./docker.md) for installation).*

## Install
Docker Compose is usually installed alongside Docker via the `docker-compose` or `docker-compose-plugin` package.

```bash
sudo apt update
sudo apt install -y docker-compose
```

## Verify

```bash
docker-compose --version
```

## How to use Docker Compose
1. Create a folder and a `docker-compose.yml` file:
```bash
mkdir myapp && cd myapp
nano docker-compose.yml
```

2. Add this example content (runs Nginx web server):
```yaml
version: '3'
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

3. Run it:
```bash
docker-compose up -d     # Start in background
docker-compose ps        # Check if it's running
docker-compose down      # Stop and remove containers
```

## Common Commands (run inside folder with docker-compose.yml)

```bash
docker-compose up -d                   # Start services in background
docker-compose up                      # Start services in foreground (shows live logs)
docker-compose down                    # Stop and remove all services/containers
docker-compose ps                      # List running services
docker-compose logs -f                 # View live logs for all services
docker-compose logs -f <service_name>  # View live logs for a specific service
docker-compose restart                 # Restart all services
docker-compose pull                    # Pull the latest versions of your images
```

## Uninstall

```bash
sudo apt purge -y docker-compose
```
