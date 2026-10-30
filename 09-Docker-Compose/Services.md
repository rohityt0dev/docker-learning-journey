# Docker Compose Services

## 🎯 Objective
Learn how to define and manage services in Docker Compose.

## 1. Example `compose.yaml`

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"

  app:
    image: httpd:latest
    ports:
      - "8081:80"
```

## 2. Start Services

```bash
docker compose up -d
```

## 3. List Services

```bash
docker compose ps
```

## 4. Stop Services

```bash
docker compose down
```

## ✅ Key Points
- Each service defines an application component.
- A service can use an image or build from a Dockerfile.
- Services can communicate using service names.