# Docker Volume Commands

## Objective

Learn the essential Docker volume commands to create, inspect, manage, and remove volumes.

## 1. Create a Volume

```bash
docker volume create my-volume
```

Creates a new Docker volume named `my-volume`.

## 2. List Volumes

```bash
docker volume ls
```

Displays all Docker volumes.

## 3. Inspect a Volume

```bash
docker volume inspect my-volume
```

Displays detailed information about the volume.

## 4. Use a Volume in a Container

```bash
docker run -d \
  --name my-nginx \
  -v my-volume:/usr/share/nginx/html \
  nginx
```

Mounts `my-volume` inside the container at `/usr/share/nginx/html`.

## 5. Create a Volume and Run a Container

```bash
docker run -d \
  --name my-app \
  --mount source=my-volume,target=/app/data \
  nginx
```

Docker creates the volume automatically if it does not already exist.

## 6. Check Volume Usage

```bash
docker system df -v
```

Displays Docker disk usage, including volume information.

## 7. Remove a Container

```bash
docker rm -f my-nginx
```

Removing the container does not remove the volume.

## 8. Remove a Volume

```bash
docker volume rm my-volume
```

The volume must not be in use by a container.

## 9. Remove Unused Volumes

```bash
docker volume prune
```

Removes unused anonymous volumes by default.

To include unused named volumes:

```bash
docker volume prune --all
```

**Warning:** These commands can permanently delete volume data. Review what is unused before pruning.

## 10. Copy Data from a Volume

```bash
docker run --rm \
  -v my-volume:/data:ro \
  alpine \
  ls -la /data
```

Mounts the volume read-only and lists its contents.

## 11. Backup a Volume

```bash
mkdir -p backups

docker run --rm \
  -v my-volume:/data:ro \
  -v "$(pwd)/backups:/backup" \
  alpine \
  tar -czf /backup/my-volume-backup.tar.gz -C /data .
```

Creates a compressed backup of the volume contents.

## Quick Reference

| Command | Purpose |
|---|---|
| `docker volume create` | Create a volume |
| `docker volume ls` | List volumes |
| `docker volume inspect` | Inspect a volume |
| `docker volume rm` | Remove a volume |
| `docker volume prune` | Remove unused anonymous volumes |
| `docker volume prune --all` | Remove unused volumes, including named volumes |
| `docker system df -v` | Inspect Docker disk usage |
| `docker run -v` | Mount a volume in a container |
| `docker run --mount` | Mount a volume using explicit options |

## Best Practices

- Use meaningful names for volumes.
- Back up important data regularly.
- Use read-only mounts when write access is unnecessary.
- Never remove a volume before confirming that its data is no longer needed.
- Test backups by restoring them to a separate volume.

## Summary

Docker volume commands help you manage persistent container storage, inspect volume usage, and back up important data.