# Docker Compose Networks

## 🎯 Objective
Learn how to connect services using Docker Compose networks.

## 1. Example `compose.yaml`

```yaml
services:
  web:
    image: nginx:latest
    networks:
      - app-network

  app:
    image: httpd:latest
    networks:
      - app-network

networks:
  app-network:
    driver: bridge
```

## 2. Start Services

```bash
docker compose up -d
```

## 3. List Networks

```bash
docker network ls
```

## 4. Cleanup

```bash
docker compose down
```

## ✅ Key Points
- Compose creates a default network when one is not specified.
- Services on the same network can communicate using service names.
- Custom networks help separate application components.