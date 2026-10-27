# Docker Container Filesystem

## Objective

Understand how a Docker container's filesystem works and how changes are stored.

## 1. What Is a Container Filesystem?

A Docker container uses the filesystem provided by its image, along with a writable layer for changes made while the container runs.

- **Image layers:** Read-only layers shared by images and containers.
- **Writable layer:** Stores changes made by a running container.
- **Volumes:** Store data independently of a container's lifecycle.

## 2. View the Container Filesystem

Start a container:

```bash
docker run -d --name my-nginx nginx
```

Open a shell inside it:

```bash
docker exec -it my-nginx sh
```

Inside the container, run:

```bash
ls /
pwd
```

Exit the container:

```bash
exit
```

## 3. Create a File Inside a Container

```bash
docker exec my-nginx sh -c "echo 'Hello Docker' > /tmp/message.txt"
```

Read the file:

```bash
docker exec my-nginx cat /tmp/message.txt
```

The file is stored in the container's writable layer.

## 4. Understand Container Data Persistence

If you remove the container, data stored only in its writable layer is lost.

```bash
docker rm -f my-nginx
```

To keep important data independently of the container, use a volume.

## 5. Use a Docker Volume

Create a volume:

```bash
docker volume create my-data
```

Start a container with the volume mounted:

```bash
docker run -d \
  --name my-nginx \
  -v my-data:/data \
  nginx
```

Files written under `/data` are stored in the volume and can persist after the container is removed.

## 6. Inspect Container Storage

```bash
# View container details
docker inspect my-nginx

# View container filesystem changes
docker diff my-nginx

# List volumes
docker volume ls
```

`docker diff` shows filesystem changes in the container's writable layer; it does not show changes to mounted volumes.

## Best Practices

- Use volumes for important persistent data.
- Avoid storing essential data only in the writable layer.
- Keep container filesystems as simple as possible.
- Use bind mounts when you need to share specific host files or directories with a container.

## Summary

A container combines read-only image layers with a writable layer. Use Docker volumes or bind mounts to store data that must survive container removal.