# Docker Exec

`docker exec` is used to **run a command inside a running Docker container**.

It is commonly used for troubleshooting, inspecting files, checking processes, and opening an interactive shell.

## Basic Syntax

```bash
docker exec [OPTIONS] CONTAINER COMMAND
```

Example:

```bash
docker exec my-nginx ls
```

This runs `ls` inside the `my-nginx` container.

## Run a Command

Example:

```bash
docker exec my-nginx pwd
```

Check the container's environment:

```bash
docker exec my-nginx env
```

Check running processes:

```bash
docker exec my-nginx ps
```

## Interactive Shell

Use `-it` to open an interactive shell:

```bash
docker exec -it my-nginx /bin/bash
```

```text
-i → Keep STDIN open
-t → Allocate a terminal
```

Exit the container shell:

```bash
exit
```

### Alpine Containers

Alpine Linux usually uses `/bin/sh` instead of Bash:

```bash
docker exec -it my-container /bin/sh
```

## Execute as a Specific User

Use `-u`:

```bash
docker exec -u root -it my-nginx /bin/bash
```

You can also specify a user ID:

```bash
docker exec -u 1000 my-nginx whoami
```

## Set Environment Variables

Use `-e`:

```bash
docker exec -e APP_ENV=production my-nginx env
```

## Run in a Specific Working Directory

Use `-w`:

```bash
docker exec -w /usr/share/nginx/html my-nginx pwd
```

## Run in Detached Mode

Use `-d` to run the command in the background:

```bash
docker exec -d my-nginx touch /tmp/test.txt
```

Check:

```bash
docker exec my-nginx ls /tmp
```

## Practical Example

Create an Nginx container:

```bash
docker run -d --name my-nginx nginx
```

Check the container:

```bash
docker ps
```

Open a shell:

```bash
docker exec -it my-nginx /bin/bash
```

Inside the container:

```bash
ls
pwd
whoami
```

Exit:

```bash
exit
```

Check Nginx processes:

```bash
docker exec my-nginx ps
```

Check Nginx configuration:

```bash
docker exec my-nginx nginx -t
```

## `docker exec` vs `docker run`

These commands have different purposes.

### `docker run`

Creates and starts a **new container**:

```bash
docker run -d --name my-nginx nginx
```

### `docker exec`

Runs a command inside an **existing running container**:

```bash
docker exec my-nginx ls
```

```text
docker run
    ↓
Create Container
    ↓
Running Container
    ↓
docker exec
    ↓
Run Command Inside Container
```

## Important Requirement

`docker exec` works only with a **running container**.

This will fail if the container is stopped:

```bash
docker exec my-nginx ls
```

Check the container:

```bash
docker ps
```

Start it if necessary:

```bash
docker start my-nginx
```

Then:

```bash
docker exec my-nginx ls
```

## Common Options

| Option | Purpose |
|---|---|
| `-i` | Keep STDIN open |
| `-t` | Allocate a terminal |
| `-it` | Interactive terminal |
| `-d` | Run command in background |
| `-u` | Run as a specific user |
| `-w` | Set working directory |
| `-e` | Set environment variable |

## Useful Troubleshooting Commands

```bash
docker exec my-nginx ps
docker exec my-nginx env
docker exec my-nginx df -h
docker exec my-nginx ls
docker exec my-nginx pwd
docker exec my-nginx whoami
```

Interactive troubleshooting:

```bash
docker exec -it my-nginx /bin/bash
```

### Key Point

> **`docker exec` lets you execute a command inside an already running container without creating a new container.**