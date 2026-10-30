# Docker Compose Depends On

## 🎯 Objective
Learn how to define service startup dependencies.

## 1. Example `compose.yaml`

```yaml
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password

  app:
    image: nginx:latest
    depends_on:
      - db
```

## 2. Start Services

```bash
docker compose up -d
```

Compose starts `db` before `app`.

## 3. Wait for Health

For applications that require a healthy database, configure a health check and use:

```yaml
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password
    healthcheck:
      test: ["CMD", "mysqladmin", "ping", "-h", "localhost", "-pexample-password"]
      interval: 10s
      timeout: 5s
      retries: 5

  app:
    image: nginx:latest
    depends_on:
      db:
        condition: service_healthy
```

## ✅ Key Points
- `depends_on` controls service startup order.
- Basic `depends_on` does not wait for a service to become ready.
- `condition: service_healthy` waits for the dependency's health check to pass.
- Applications should still handle connection failures and retries.