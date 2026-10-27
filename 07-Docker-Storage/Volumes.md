# Docker Volumes

## Objective
Learn how to store and persist container data using Docker volumes.

## 1. What Is a Docker Volume?

A Docker volume stores data independently of a container's lifecycle. It allows data to persist even when a container is removed.

## 2. Create a Volume

```bash
docker volume create my-data
```

## 3. List Volumes

```bash
docker volume ls
```

## 4. Inspect a Volume

```bash
docker volume inspect my-data
```

## 5. Use a Volume in a Container

```bash
docker run -d \
  --name my-nginx \
  -v my-data:/usr/share/nginx/html \
  nginx
```

- `my-data` — Docker volume name
- `/usr/share/nginx/html` — Mount path inside the container

## 6. Test Data Persistence

Create a file in the mounted volume:

```bash
docker exec my-nginx sh -c \
  "echo 'Hello from Docker Volume' > /usr/share/nginx/html/index.html"
```

Remove the container:

```bash
docker rm -f my-nginx
```

Create another container using the same volume:

```bash
docker run -d \
  --name my-nginx-new \
  -p 8080:80 \
  -v my-data:/usr/share/nginx/html \
  nginx
```

Open `http://localhost:8080` to verify that the data persists.

## 7. Remove a Volume

Remove a volume when it is no longer needed:

```bash
docker volume rm my-data
```

Docker cannot remove a volume while it is in use by a container.

## Best Practices

- Use volumes for important persistent data.
- Use meaningful volume names.
- Back up important volume data regularly.
- Avoid deleting volumes that contain required data.
- Remember that mounting a volume over a non-empty container directory can hide the directory's existing contents.

## Summary

Docker volumes provide persistent storage for containers. Data stored in a volume can survive container removal and be reused by other containers.