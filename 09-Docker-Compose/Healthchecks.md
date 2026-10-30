# Docker Compose Health Checks

## 🎯 Objective
Learn how to check whether a service is healthy.

## 1. Example `compose.yaml`

```yaml
services:
  web:
    image: nginx:latest
    healthcheck:
      test: ["CMD-SHELL", "curl -f http://localhost/ || exit 1"]
      interval: 30s
      timeout: 5s
      retries: 3
      start_period: 10s
```

**Note:** The official Nginx image may not include `curl`. Use a health-check command supported by your image.

## 2. Start Service

```bash
docker compose up -d
```

## 3. Check Status

```bash
docker compose ps
```

## 4. Inspect Health

```bash
docker inspect --format='{{.State.Health.Status}}' <container-name>
```

## ✅ Key Points
- `interval` sets how often checks run.
- `timeout` sets the maximum time for a check.
- `retries` sets the failures needed to mark a container unhealthy.
- `start_period` allows time for application startup.
- Health checks report status; they do not automatically repair an unhealthy application.