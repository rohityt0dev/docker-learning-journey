# Dockerfile Basics

A **Dockerfile** is a text file containing instructions to build a Docker image.

## Basic Dockerfile

Create a file named `Dockerfile`:

```dockerfile
FROM nginx:alpine
COPY index.html /usr/share/nginx/html/index.html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

## Main Instructions

| Instruction | Description |
|---|---|
| `FROM` | Specifies the base image |
| `RUN` | Executes commands during image building |
| `COPY` | Copies files into the image |
| `ADD` | Copies files or extracts local archives |
| `WORKDIR` | Sets the working directory |
| `ENV` | Sets environment variables |
| `EXPOSE` | Documents the container port |
| `CMD` | Specifies the default command |
| `ENTRYPOINT` | Defines the main executable |

## Build a Docker Image

Run this command in the directory containing your Dockerfile and `index.html`:

```bash
docker build -t my-web:v1 .
```

- `-t my-web:v1` assigns the image name and tag.
- `.` specifies the build context.

## Run the Container

```bash
docker run -d --name my-web -p 8080:80 my-web:v1
```

Open in your browser:

```text
http://localhost:8080
```

## View and Manage

List images:

```bash
docker images
```

List running containers:

```bash
docker ps
```

View logs:

```bash
docker logs my-web
```

Remove the test container:

```bash
docker rm -f my-web
```

## Best Practices

- Use small, trusted base images.
- Use `.dockerignore` to exclude unnecessary files.
- Combine related commands to reduce unnecessary layers.
- Avoid storing passwords or secrets in images.
- Use specific image tags instead of relying on `latest`.

### Key Point

> **A Dockerfile defines how to build an image, and the resulting image is used to create containers.**