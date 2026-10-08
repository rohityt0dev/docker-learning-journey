# Docker PS

`docker ps` is used to **list running Docker containers**.

## Basic Command

```bash
docker ps
```

Example output:

```text
CONTAINER ID   IMAGE   COMMAND                  CREATED        STATUS        PORTS                  NAMES
a1b2c3d4e5f6   nginx   "/docker-entrypoint…"   2 minutes ago  Up 2 minutes  0.0.0.0:8080->80/tcp   my-nginx
```

## Understanding the Output

| Column | Description |
|---|---|
| `CONTAINER ID` | Unique container identifier |
| `IMAGE` | Image used to create the container |
| `COMMAND` | Command running inside the container |
| `CREATED` | Time since the container was created |
| `STATUS` | Current container status |
| `PORTS` | Port mappings |
| `NAMES` | Container name |

## List All Containers

By default, `docker ps` shows only running containers.

To show **running and stopped containers**:

```bash
docker ps -a
```

Example:

```text
CONTAINER ID   IMAGE   STATUS
a1b2c3d4e5f6   nginx   Up 5 minutes
b2c3d4e5f6a7   ubuntu  Exited (0) 10 minutes ago
```

## Show Only Container IDs

```bash
docker ps -q
```

Example:

```text
a1b2c3d4e5f6
b2c3d4e5f6a7
```

Useful for scripting.

## Show Latest Container

```bash
docker ps -l
```

Shows the most recently created container.

## Show Latest N Containers

```bash
docker ps -n 3
```

Shows the last 3 created containers.


## Display Container Size

Use `-s`:

```bash
docker ps -s
```

This shows the container's writable layer size.

## Common Options

| Command | Purpose |
|---|---|
| `docker ps` | Show running containers |
| `docker ps -a` | Show all containers |
| `docker ps -q` | Show container IDs |
| `docker ps -l` | Show latest container |
| `docker ps -n 3` | Show latest 3 containers |
| `docker ps -s` | Show container size |

### Key Point

> **`docker ps` shows running containers, while `docker ps -a` shows all containers, including stopped containers.**