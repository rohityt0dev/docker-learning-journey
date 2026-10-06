# Container Basics

A **container** is a lightweight, isolated environment used to run an application and its dependencies.

Containers are created from **Docker images**.

```text
Docker Image
     ↓
  Container
     ↓
 Application
```

## Create and Run a Container

Run an Nginx container:

```bash
docker run nginx
```

Run in the background:

```bash
docker run -d nginx
```

Give the container a name:

```bash
docker run -d --name my-nginx nginx
```

## List Containers

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

## Start and Stop Containers

Start:

```bash
docker start my-nginx
```

Stop:

```bash
docker stop my-nginx
```

Restart:

```bash
docker restart my-nginx
```

## Remove a Container

Remove a stopped container:

```bash
docker rm my-nginx
```

Force remove a running container:

```bash
docker rm -f my-nginx
```

## Container Logs

View logs:

```bash
docker logs my-nginx
```

Follow logs:

```bash
docker logs -f my-nginx
```

## Execute Commands

Run a command inside a container:

```bash
docker exec my-nginx ls
```

Open a shell:

```bash
docker exec -it my-nginx /bin/bash
```

For Alpine containers:

```bash
docker exec -it my-nginx /bin/sh
```

## Port Mapping

Containers have their own network namespace. To access a container service from the host, map a port.

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

```text
Host
Port 8080
   ↓
Container
Port 80
   ↓
Nginx
```

Open:

```text
http://<EC2-PUBLIC-IP>:8080
```

> Make sure the EC2 security group allows inbound TCP traffic on port `8080`.

## Container Naming

Without a name:

```bash
docker run -d nginx
```

Docker automatically generates a container name.

With a custom name:

```bash
docker run -d --name web-server nginx
```

Then use:

```bash
docker stop web-server
docker start web-server
docker logs web-server
```

## Useful Commands

| Command | Purpose |
|---|---|
| `docker run` | Create and start a container |
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker start` | Start a container |
| `docker stop` | Stop a container |
| `docker restart` | Restart a container |
| `docker rm` | Remove a container |
| `docker logs` | View container logs |
| `docker exec` | Execute a command inside a container |
| `docker inspect` | View container details |

## Container Lifecycle

```text
        docker run
             ↓
          Created
             ↓
          Running
          ↙     ↘
   docker stop  docker restart
        ↓            ↓
      Stopped ←──────┘
        ↓
    docker rm
        ↓
     Removed
```

## Image vs Container

| Image | Container |
|---|---|
| Template | Running instance |
| Read-only | Writable container layer |
| Used to create containers | Runs the application |
| `docker images` | `docker ps` |

### Key Point

> **An image is the template, while a container is the running instance of that image.**
