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

## Run in Detached Mode

Use `-d` to run the command in the background:

```bash
docker exec -d my-nginx touch /tmp/test.txt
```

Check:

```bash
docker exec my-nginx ls /tmp
```

### Key Point

> **`docker exec` lets you execute a command inside an already running container without creating a new container.**