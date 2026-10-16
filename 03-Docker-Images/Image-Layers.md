# Docker Image Layers

Docker images are built using **multiple layers**. Each instruction in a Dockerfile can create a layer, and Docker reuses unchanged layers to make image builds faster.

## Image Layer Architecture

```text
       Docker Image
    ┌───────────────────┐
    │ Application Code  │
    ├───────────────────┤
    │ Dependencies      │
    ├───────────────────┤
    │ Installed Packages│
    ├───────────────────┤
    │ Base Image        │
    └───────────────────┘
```

Each layer adds filesystem changes to the image.

## Example Dockerfile

```dockerfile
FROM ubuntu:24.04
RUN apt-get update
RUN apt-get install -y nginx
COPY index.html /var/www/html/index.html
CMD ["nginx", "-g", "daemon off;"]
```

Docker creates reusable filesystem layers for build instructions such as `RUN` and `COPY`. `CMD` specifies the default command and does not create a filesystem layer by itself.

## How Layers Work

- **Read-only:** Image layers are immutable.
- **Reusable:** Multiple images can share the same base layers.
- **Cached:** Docker can reuse unchanged build steps.
- **Efficient:** Only changed layers and required dependent steps need rebuilding.

## View Image Layers

Display image build history:

```bash
docker image history nginx
```

Inspect image details:

```bash
docker image inspect nginx
```

List local images:

```bash
docker images
```

## Layer Caching Example

Consider this Dockerfile:

```dockerfile
FROM ubuntu:24.04
RUN apt-get update
RUN apt-get install -y nginx
COPY index.html /var/www/html/index.html
```

If only `index.html` changes, Docker can reuse earlier cached layers when their inputs and build conditions remain unchanged.

**Best practice:** Place instructions that change less frequently before instructions that change frequently.

## Image Layers vs Container Layer

| Image Layers | Container Layer |
|---|---|
| Read-only | Writable by default |
| Shared between images when possible | Belongs to a specific container |
| Created during image building | Created when a container is created |
| Remain unchanged | Stores runtime filesystem changes |

Changes made inside a container do not modify the original image.

## Best Practices

- Use small, trusted base images.
- Combine related commands where appropriate.
- Remove package-manager caches and temporary files in the same `RUN` instruction.
- Order Dockerfile instructions to improve cache reuse.
- Use `.dockerignore` to exclude unnecessary build-context files.

### Key Point

> **Docker image layers make images efficient through caching and reuse. Image layers are read-only, while a container normally adds its own writable layer.**