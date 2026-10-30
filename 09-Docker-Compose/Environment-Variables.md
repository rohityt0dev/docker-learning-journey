# Docker Compose Environment Variables

## 🎯 Objective
Learn how to configure services using environment variables.

## 1. Example `compose.yaml`

```yaml
services:
  app:
    image: nginx:latest
    environment:
      APP_ENV: production
      APP_PORT: "8080"
```

## 2. Use an `.env` File

Create `.env`:

```dotenv
APP_ENV=production
APP_PORT=8080
```

Update `compose.yaml`:

```yaml
services:
  app:
    image: nginx:latest
    environment:
      APP_ENV: ${APP_ENV}
      APP_PORT: ${APP_PORT}
```

## 3. Start Services

```bash
docker compose up -d
```

## 4. Verify Variables

```bash
docker compose exec app printenv APP_ENV
```

## ✅ Key Points
- `environment` sets variables inside a container.
- Compose can substitute values from an `.env` file.
- Add `.env` to `.gitignore` if it contains sensitive values.
- Use secrets for sensitive credentials where supported.