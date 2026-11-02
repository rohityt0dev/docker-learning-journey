# Nginx and Application with Docker

## 🎯 Objective
Learn how Nginx can act as a reverse proxy for an application.

## 1. Create `compose.yaml`

```yaml
services:
  nginx:
    image: nginx:alpine
    ports:
      - "8080:80"
    volumes:
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
    depends_on:
      - app

  app:
    image: httpd:alpine
```

## 2. Create `nginx.conf`

```nginx
server {
    listen 80;

    location / {
        proxy_pass http://app:80;
    }
}
```

## 3. Start Services

```bash
docker compose up -d
```

Open `http://localhost:8080`.

## 4. Cleanup

```bash
docker compose down
```

## ✅ Key Points
- Nginx receives requests on port `8080` of the host.
- Nginx forwards requests to the `app` service on port `80`.
- Both services communicate through the Compose network.
- The example proxies requests to Apache HTTP Server.