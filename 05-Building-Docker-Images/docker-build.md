# Docker Build Command

## Objective
Learn how to build a Docker image from a `Dockerfile`.

## Syntax

```bash
docker build -t image-name:tag .
```

- `docker build` — Builds a Docker image.
- `-t` — Assigns an image name and tag.
- `.` — Specifies the current directory as the build context.

## Example

**Dockerfile**
```dockerfile
FROM nginx:latest
COPY index.html /usr/share/nginx/html/index.html
```

**Build the image**
```bash
docker build -t my-nginx:v1 .
```

**List images**
```bash
docker images
```

**Run the container**
```bash
docker run -d --name my-container -p 8080:80 my-nginx:v1
```

Open `http://localhost:8080` in your browser.

## Useful Build Commands

```bash
# Build with a custom Dockerfile
docker build -f Dockerfile.dev -t my-app:dev .


## Important Notes

- A `Dockerfile` contains the instructions to build an image.
- The build context contains the files Docker can access during the build.
- Use `.dockerignore` to exclude unnecessary files from the build context.
- Use meaningful image tags such as `v1`, `v2`, or `latest`.

## Summary

The `docker build` command creates a Docker image using a Dockerfile and build context.