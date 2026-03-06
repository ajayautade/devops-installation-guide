# 🔍 SonarQube

> Default port: **9000** — open in EC2 Security Group | Requires Docker

## Install (Docker — fastest way)

```bash
docker run -d --name sonarqube -p 9000:9000 sonarqube:lts-community
```

## Access

- URL: `http://<EC2_PUBLIC_IP>:9000`
- Username: `admin` | Password: `admin` (change on first login)

## With Docker Compose (Persistent + PostgreSQL)

```bash
mkdir ~/sonarqube && cd ~/sonarqube
```

Create `docker-compose.yml`:
```yaml
version: "3"
services:
  sonarqube:
    image: sonarqube:lts-community
    depends_on: [db]
    environment:
      SONAR_JDBC_URL: jdbc:postgresql://db:5432/sonar
      SONAR_JDBC_USERNAME: sonar
      SONAR_JDBC_PASSWORD: sonar
    ports: ["9000:9000"]
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
  db:
    image: postgres:15
    environment:
      POSTGRES_USER: sonar
      POSTGRES_PASSWORD: sonar
      POSTGRES_DB: sonar
    volumes: [postgresql_data:/var/lib/postgresql/data]

volumes:
  sonarqube_data:
  sonarqube_extensions:
  postgresql_data:
```

```bash
# Required kernel params
sudo sysctl -w vm.max_map_count=524288
echo "vm.max_map_count=524288" | sudo tee -a /etc/sysctl.conf

docker compose up -d
```

## Common Commands

```bash
docker start/stop/restart sonarqube
docker logs -f sonarqube
```

## Uninstall

```bash
docker stop sonarqube && docker rm sonarqube
# Or with compose: docker compose down -v
```
