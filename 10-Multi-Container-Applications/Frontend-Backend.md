# Frontend and Backend with Docker

## 🎯 Objective
Learn how frontend and backend services communicate.

## 1. Example `compose.yaml`

```yaml
services:
  frontend:
    image: nginx:alpine
    ports:
      - "8080:80"

  backend:
    image: httpd:alpine
    expose:
      - "80"
```

## 2. Start Services

```bash
docker compose up -d
```

## 3. Verify Services

```bash
docker compose ps
docker compose logs
```

## ✅ Key Points
- Compose creates a default network for the services.
- Services can discover each other using service names.
- `expose` documents an internal port; it does not publish the port to the host.
- This example runs both services but does not configure actual frontend-to-backend integration. Application code or a reverse proxy must be configured for that.