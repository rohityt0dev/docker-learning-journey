# Docker Run

`docker run` is used to **create and start a new Docker container from an image**.

## Basic Syntax

```bash
docker run [OPTIONS] IMAGE [COMMAND]
```

Example:

```bash
docker run nginx
```

Docker will:

```text
Docker Image
     ↓
docker run
     ↓
Create Container
     ↓
Start Container
```

## Run a Container in Background

Use `-d` (detached mode):

```bash
docker run -d nginx
```

The container runs in the background.

Check it:

```bash
docker ps
```

## Give the Container a Name

Use `--name`:

```bash
docker run -d --name my-nginx nginx
```

Now you can use the name:

```bash
docker stop my-nginx
docker start my-nginx
docker logs my-nginx
```

## Port Mapping

Use `-p` to map a host port to a container port:

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

```text
Host                  Container
8080  ─────────────→  80
                      ↓
                    Nginx
```

For an EC2 instance:

```text
http://<EC2-PUBLIC-IP>:8080
```

> Make sure the EC2 Security Group allows inbound TCP traffic on port `8080`.

## Automatically Remove Container

Use `--rm`:

```bash
docker run --rm nginx
```

The container is automatically removed when it stops.

Useful for temporary containers.

## Interactive Container

Use `-it` to run an interactive shell:

```bash
docker run -it ubuntu /bin/bash
```

```text
-i → Keep STDIN open
-t → Allocate a terminal
```

For Alpine:

```bash
docker run -it alpine /bin/sh
```

## Run a Command

You can run a command directly inside a new container:

```bash
docker run ubuntu ls
```

Example:

```bash
docker run ubuntu echo "Hello Docker"
```

## Environment Variables

Use `-e` to set an environment variable:

```bash
docker run -d --name my-app -e App_ENV=production nginx
```

Check the variable:

```bash
docker exec my-app printenv App_ENV
```

## Volume Mount

Use `-v` to mount a host directory into a container:

```bash
docker run -d --name my-nginx -v /home/ec2-user/html:/usr/share/nginx/html nginx
```

```text
Host Directory
/home/ec2-user/html
        ↓
Container Directory
/usr/share/nginx/html
```

## Common `docker run` Options

| Option | Purpose |
|---|---|
| `-d` | Run in background |
| `-it` | Interactive terminal |
| `--name` | Assign container name |
| `-p` | Map ports |
| `-e` | Set environment variable |
| `-v` | Mount volume |
| `--rm` | Remove container after it stops |
| `--restart` | Configure restart policy |

### Key Point

> **`docker run` creates a new container from an image and starts it.**