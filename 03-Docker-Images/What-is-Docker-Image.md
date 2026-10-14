# What Is a Docker Image?

A **Docker image** is a read-only template used to create Docker containers. It contains the application code, dependencies, libraries, and configuration required to run an application.

## Docker Image Workflow

```text
Dockerfile
    ↓
Docker Image
    ↓
Docker Container
    ↓
Running Application
```

## Key Components

| Component | Description |
|---|---|
| **Image** | Template used to create containers |
| **Container** | Running instance of an image |
| **Dockerfile** | Instructions to build an image |
| **Image Registry** | Stores and distributes images |

## List Docker Images

```bash
docker images
```

Alternative command:

```bash
docker image ls
```

## Download an Image

Download the Nginx image from Docker Hub:

```bash
docker pull nginx
```

## Run a Container from an Image

```bash
docker run -d --name my-nginx nginx
```

This creates and starts a container using the `nginx` image.

## Remove an Image

```bash
docker rmi nginx
```

> The image cannot be removed if a container still references it, unless you first remove the relevant containers.

## Image Naming

Docker images commonly use this format:

```text
[REGISTRY/]REPOSITORY[:TAG]
```

Example:

```text
nginx:latest
ubuntu:24.04
```

- **Registry:** Where the image is stored.
- **Repository:** The image name.
- **Tag:** Identifies a particular version or variant.

If no tag is specified, Docker generally uses `latest` by default. The `latest` tag does not necessarily mean the newest version.

## Docker Image vs Container

| Docker Image | Docker Container |
|---|---|
| Read-only template | Created from an image |
| Used to create containers | Runs the application |
| `docker images` | `docker ps` |
| Built or downloaded | Created and started |

## Useful Commands

```bash
docker images
docker pull nginx
docker image inspect nginx
docker image history nginx
docker tag nginx my-nginx:v1
docker rmi nginx
```

### Key Point

> **A Docker image is a packaged template, while a Docker container is an instance created from that image.**