# Docker Compose Basics

## 🎯 Objective
Learn how to define and run multi-container applications using Docker Compose.

## 1. What Is Docker Compose?

Docker Compose is a tool for defining and managing multi-container applications using a YAML configuration file, usually `compose.yaml`.

## 2. Create `compose.yaml`

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

## 3. Start Services

```bash
docker compose up -d
```

## 4. Check Running Services

```bash
docker compose ps
```

## 5. View Logs

```bash
docker compose logs
```

## 6. Stop and Remove Services

```bash
docker compose down
```

## 7. Access Applications

- Nginx: `http://localhost:8080`
- Apache HTTP Server: `http://localhost:8081`

## ✅ Key Points

- `compose.yaml` defines application services and their configuration.
- `docker compose up -d` starts services in the background.
- Services on the same Compose network can communicate using service names.
- `docker compose down` removes project containers and networks.