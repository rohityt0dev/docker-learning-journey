# Docker Compose Up

## 🎯 Objective
Learn how to build and start services using Docker Compose.

## 1. Example `compose.yaml`

```yaml
services:
  web:
    image: nginx:latest
    ports:
      - "8080:80"
```

## 2. Start Services

```bash
docker compose up
```

Run in the background:

```bash
docker compose up -d
```

Build images before starting:

```bash
docker compose up -d --build
```

## 3. Check Running Services

```bash
docker compose ps
```

View logs:

```bash
docker compose logs
```

## 4. Test Application

Open in your browser:

```text
http://localhost:8080
```

## ✅ Key Points
- `docker compose up` creates and starts services.
- `-d` runs services in the background.
- `--build` builds images before starting services.
- Run the command from the directory containing `compose.yaml`.