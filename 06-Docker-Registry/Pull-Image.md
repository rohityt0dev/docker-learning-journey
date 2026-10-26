# Pull Docker Image

## Objective

Learn how to download Docker images from Docker Hub or another container registry.

## 1. What Is `docker pull`?

The `docker pull` command downloads an image from a registry to your local machine.

## 2. Pull an Image from Docker Hub

```bash
docker pull nginx
```

Pull a specific version:

```bash
docker pull nginx:1.27
```

## 3. Pull a Specific User's Image

Replace `your-username` with the image owner's Docker Hub username.

```bash
docker pull your-username/my-app:v1
```

## 4. List Downloaded Images

```bash
docker images
```

This displays the images available locally.

## 5. Run the Pulled Image

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

Open `http://localhost:8080` in your browser to access the Nginx welcome page.

## 6. Pull from a Private Repository

Log in first:

```bash
docker login
```

Then pull the image:

```bash
docker pull your-username/my-private-app:v1
```

You need permission to access the private repository.

## 7. Useful Commands

```bash
# Pull a specific tag
docker pull nginx:1.27

# View local images
docker images

# Inspect image details
docker image inspect nginx:1.27

# Remove a local image
docker rmi nginx:1.27
```

## Important Notes

- If no tag is specified, Docker uses the `latest` tag by default.
- The `latest` tag does not guarantee the newest software version.
- Pulling an image downloads it; it does not automatically start a container.
- Private images require authentication and appropriate permissions.

## Summary

The `docker pull` command downloads images from a registry so you can run containers locally.

**Workflow:** Pull → Verify → Run