# Docker Compose Down

## 🎯 Objective
Learn how to stop and remove services created by Docker Compose.

## 1. Stop and Remove Services

```bash
docker compose down
```

## 2. Stop Without Removing Containers

```bash
docker compose stop
```

## 3. Remove Containers and Images

```bash
docker compose down --rmi all
```

## 4. Remove Containers and Volumes

```bash
docker compose down --volumes
```

**Warning:** `--volumes` removes project-managed named and anonymous volumes. Persistent data stored in those volumes may be lost.

## 5. Verify Containers

```bash
docker compose ps -a
```

## ✅ Key Points
- `down` stops and removes project containers and networks.
- `stop` stops containers without removing them.
- `--rmi all` removes service images.
- `--volumes` removes associated volumes.
- Run commands from the directory containing your Compose file.