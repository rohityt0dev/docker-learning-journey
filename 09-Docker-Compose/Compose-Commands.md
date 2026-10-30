# Docker Compose Commands

## 🎯 Objective
Learn essential Docker Compose commands to manage multi-container applications.

## 1. Start Services

```bash
docker compose up
docker compose up -d
```

## 2. Stop and Remove Services

```bash
docker compose down
docker compose stop
docker compose start
```

## 3. Check Services

```bash
docker compose ps
docker compose logs
docker compose logs -f
```

## 4. Build Images

```bash
docker compose build
docker compose up -d --build
```

## 5. Execute Commands

```bash
docker compose exec web sh
docker compose run --rm web sh
```

- `exec` runs a command inside an existing service container.
- `run` creates a one-off container for a service.

## 6. View Configuration

```bash
docker compose config
```

## 7. Pull Images

```bash
docker compose pull
```

## 8. Restart Services

```bash
docker compose restart
```

## 9. Remove Unused Resources

```bash
docker compose down --volumes
```

**Warning:** This removes associated Compose-managed volumes and may permanently delete stored data.

## ✅ Key Points

- Run commands from the directory containing `compose.yaml`.
- Use `-d` to run services in the background.
- Use `docker compose logs -f` to follow logs.
- Use `docker compose ps` to check service status.
- Use `docker compose down` to stop and remove project containers and networks.