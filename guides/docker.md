# 🐳 Docker

## Install

```bash
sudo apt update
sudo apt install -y docker.io docker-compose
sudo systemctl start docker
sudo systemctl enable docker

# Run Docker without sudo
sudo usermod -aG docker $USER
newgrp docker
```

## Verify

```bash
docker --version
docker-compose --version
docker run hello-world
```

## Common Commands

```bash
docker ps                              # Running containers
docker ps -a                           # All containers
docker images                          # List images
docker pull <image>                    # Pull image
docker build -t <tag> .                # Build image
docker run -d -p 8080:80 <image>       # Run container
docker stop <id>                       # Stop container
docker rm <id>                         # Remove container
docker rmi <image>                     # Remove image
docker logs <id>                       # View logs
docker exec -it <id> bash              # Shell into container
docker-compose up -d                   # Start compose services
docker-compose down                    # Stop compose services
docker system prune -a                 # Clean everything
```

## Uninstall

```bash
sudo apt purge -y docker.io docker-compose
sudo rm -rf /var/lib/docker
```
