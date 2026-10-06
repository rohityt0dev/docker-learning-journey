# Docker CLI

Docker CLI (Command Line Interface) is used to **interact with Docker Engine** and manage containers, images, networks, and volumes.

## Basic Syntax

```bash
docker [command] [options]
```

Example:

```bash
docker ps
```

## Docker Information

```bash
docker version
docker info
docker --help
```

## Image Commands

List images:

```bash
docker images
```

Download an image:

```bash
docker pull nginx
```

Remove an image:

```bash
docker rmi nginx
```

Build an image:

```bash
docker build -t myapp .
```

## Container Commands

Run a container:

```bash
docker run nginx
```

Run in background:

```bash
docker run -d nginx
```

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

Stop a container:

```bash
docker stop <container-id>
```

Start a stopped container:

```bash
docker start <container-id>
```

Restart a container:

```bash
docker restart <container-id>
```

Remove a container:

```bash
docker rm <container-id>
```

## Container Logs

View logs:

```bash
docker logs <container-id>
```

Follow logs:

```bash
docker logs -f <container-id>
```

## Execute Commands

Run a command inside a running container:

```bash
docker exec <container-id> <command>
```

Open an interactive shell:

```bash
docker exec -it <container-id> /bin/bash
```

For Alpine images:

```bash
docker exec -it <container-id> /bin/sh
```

## Port Mapping

Map host port `8080` to container port `80`:

```bash
docker run -d -p 8080:80 nginx
```

```text
Host:      8080
             ↓
Container:  80
```

## Useful Commands

| Command | Purpose |
|---|---|
| `docker ps` | List running containers |
| `docker images` | List images |
| `docker pull` | Download image |
| `docker build` | Build image |
| `docker run` | Create and start container |
| `docker start` | Start container |
| `docker stop` | Stop container |
| `docker restart` | Restart container |
| `docker logs` | View container logs |
| `docker exec` | Execute command in container |
| `docker rm` | Remove container |
| `docker rmi` | Remove image |

## Basic Workflow

```text
Pull / Build Image
       ↓
   docker run
       ↓
    Container
       ↓
docker ps / logs / exec
       ↓
docker stop
       ↓
docker rm
```

### Key Point

> **Docker CLI provides the commands used to communicate with Docker Engine and manage Docker resources.**