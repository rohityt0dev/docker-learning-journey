# Docker Image Commands

Docker image commands are used to download, list, inspect, build, tag, and remove Docker images.

## 1. List Images

Display all local images:

```bash
docker images
```

Alternative:

```bash
docker image ls
```

## 2. Download an Image

Download Nginx from Docker Hub:

```bash
docker pull nginx
```

Download a specific version:

```bash
docker pull nginx:alpine
```

## 3. Inspect an Image

View detailed image information:

```bash
docker image inspect nginx
```

Display image history and layers:

```bash
docker image history nginx
```

## 4. Build an Image

Build an image using a Dockerfile in the current directory:

```bash
docker build -t my-app:v1 .
```

- `-t` assigns an image name and tag.
- `.` specifies the build context.

## 5. Tag an Image

Create another tag for an existing image:

```bash
docker tag nginx my-nginx:v1
```

List images:

```bash
docker images
```

## 6. Remove an Image

Remove an image by name:

```bash
docker rmi nginx
```

Remove an image by ID:

```bash
docker rmi <image-id>
```

Docker cannot normally remove an image referenced by existing containers.

## 7. Remove Unused Images

Remove dangling images:

```bash
docker image prune
```

Remove all images not used by existing containers:

```bash
docker image prune -a
```

**Warning:** Review the cleanup scope before running prune commands.


## 8. Search Docker Hub

Search for images:

```bash
docker search nginx
```

## Useful Commands Summary

| Command | Purpose |
|---|---|
| `docker images` | List local images |
| `docker pull nginx` | Download an image |
| `docker image inspect nginx` | View image details |
| `docker image history nginx` | View image history |
| `docker build -t my-app:v1 .` | Build an image |
| `docker tag nginx my-nginx:v1` | Tag an image |
| `docker rmi nginx` | Remove an image |
| `docker image prune` | Remove dangling images |
| `docker search nginx` | Search Docker Hub |

### Key Point

> **Docker image commands help you manage the complete image workflow, from downloading and building images to inspecting, tagging, saving, and removing them.**