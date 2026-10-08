# Docker Start and Stop

Docker provides commands to **start, stop, restart, and manage the state of containers**.

## Start a Container

Start an existing stopped container:

```bash
docker start my-nginx
```

Check:

```bash
docker ps
```

## Start Multiple Containers

```bash
docker start container1 container2 container3
```

## Start in Attached Mode

By default, `docker start` starts the container in the background.

Use `-a` to attach to the container's output:

```bash
docker start -a my-nginx
```

---

## Stop a Container

Stop a running container gracefully:

```bash
docker stop my-nginx
```

Docker sends a termination signal and gives the application time to shut down.

Check:

```bash
docker ps
```

The container will no longer appear because it is stopped.

To see it:

```bash
docker ps -a
```

## Stop Multiple Containers

```bash
docker stop container1 container2 container3
```

---

## Restart a Container

Restart a running or stopped container:

```bash
docker restart my-nginx
```

You can also specify a timeout:

```bash
docker restart -t 30 my-nginx
```

Basic lifecycle:

```text
Running
   ↓
docker restart
   ↓
Stopped
   ↓
Started
   ↓
Running
```

---

## Kill a Container

`docker kill` immediately terminates the container's main process.

```bash
docker kill my-nginx
```

### `stop` vs `kill`

| Command | Behavior |
|---|---|
| `docker stop` | Graceful shutdown |
| `docker kill` | Immediate termination |

Prefer `docker stop` when possible.

---

## Start vs Run

These commands are different.

### `docker run`

Creates **and starts a new container**:

```bash
docker run -d --name my-nginx nginx
```

### `docker start`

Starts an **existing stopped container**:

```bash
docker start my-nginx
```

```text
docker run
    ↓
Create new container
    ↓
Start container


docker start
    ↓
Existing container
    ↓
Start container
```

---

### Key Point

> **`docker run` creates a new container, `docker start` starts an existing container, and `docker stop` gracefully stops a running container.**