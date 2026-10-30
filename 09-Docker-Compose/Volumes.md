# Docker Compose Volumes

## 🎯 Objective
Learn how to persist data using Docker Compose volumes.

## 1. Example `compose.yaml`

```yaml
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password
    volumes:
      - db-data:/var/lib/mysql

volumes:
  db-data:
```

## 2. Start Service

```bash
docker compose up -d
```

## 3. List Volumes

```bash
docker volume ls
```

## 4. Cleanup

```bash
docker compose down
```

**Note:** The named volume remains after `down`. Use `docker compose down --volumes` to remove Compose-managed volumes.

## ✅ Key Points
- Volumes preserve data beyond a container's lifecycle.
- Named volumes are useful for databases.
- Removing a volume can permanently delete its data.