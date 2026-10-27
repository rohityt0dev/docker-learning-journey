# Docker tmpfs Mounts

## Objective

Learn how to use `tmpfs` mounts to store temporary data in memory instead of writing it to the container's writable layer.

## 1. What Is a tmpfs Mount?

A **tmpfs mount** stores temporary files in memory on the Docker host. The data is not persisted when the container stops or the host reboots.

### Key Features

- Stores temporary data in memory.
- Does not persist data after the container stops.
- Useful for temporary files and sensitive data that should not be written to the container's writable layer.
- Available on Linux Docker hosts.

## 2. Create a Container with a tmpfs Mount

```bash
docker run -d \
  --name my-nginx \
  --mount type=tmpfs,dst=/app/temp \
  nginx
```

This mounts a temporary filesystem at `/app/temp` inside the container.

## 3. Write Data to the tmpfs Mount

```bash
docker exec my-nginx sh -c \
  "echo 'Temporary Docker Data' > /app/temp/message.txt"
```

Read the file:

```bash
docker exec my-nginx cat /app/temp/message.txt
```

Expected output:

```text
Temporary Docker Data
```

## 4. Set the tmpfs Size

```bash
docker run -d \
  --name tmpfs-app \
  --mount type=tmpfs,dst=/app/temp,tmpfs-size=64m \
  nginx
```

`tmpfs-size=64m` sets a maximum size of 64 MiB for the tmpfs mount.

## 5. Use the `--tmpfs` Option

You can also create a tmpfs mount using `--tmpfs`:

```bash
docker run -d \
  --name tmpfs-nginx \
  --tmpfs /app/temp:rw,size=64m \
  nginx
```

- `rw` — Allows reading and writing.
- `size=64m` — Sets the maximum size to 64 MiB.

## 6. Inspect the Container

```bash
docker inspect tmpfs-app
```

Check the `Mounts` section for mount information.

## 7. Test Data Persistence

Stop the container:

```bash
docker stop tmpfs-app
```

Start it again:

```bash
docker start tmpfs-app
```

Check whether the file exists:

```bash
docker exec tmpfs-app ls -la /app/temp
```

**Important:** On Linux, tmpfs data is removed when the container stops. Do not use tmpfs for data that must survive container restarts.

## Bind Mount vs Volume vs tmpfs

| Feature | Bind Mount | Docker Volume | tmpfs Mount |
|---|---|---|---|
| Storage | Host filesystem path | Docker-managed storage | Memory |
| Data persists after container removal | Yes, on host | Yes | No |
| Typical use | Development and file sharing | Persistent application data | Temporary data |
| Host file access | Direct | Through Docker-managed storage | Not as a normal host directory |

## Best Practices

- Use tmpfs for temporary data only.
- Do not store important files that must persist.
- Set an appropriate size limit.
- Remember that memory-backed storage is not automatically secure against every form of data exposure.
- Use volumes or bind mounts when data must persist.

## Summary

Docker tmpfs mounts store temporary data in memory rather than in the container's writable layer. They are useful for workloads that need fast, non-persistent storage.