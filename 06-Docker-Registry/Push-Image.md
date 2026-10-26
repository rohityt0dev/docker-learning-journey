# Push Docker Image to Docker Hub

## Objective

Learn how to tag and push a Docker image to Docker Hub.

## 1. Build a Docker Image

Run this command in the directory containing your `Dockerfile`:

```bash
docker build -t my-app:v1 .
```

## 2. Login to Docker Hub

```bash
docker login
```

Authenticate using your Docker Hub credentials.

## 3. Tag the Image

Replace `your-username` with your Docker Hub username.

```bash
docker tag my-app:v1 your-username/my-app:v1
```

## 4. Push the Image

```bash
docker push your-username/my-app:v1
```

Docker uploads the image to your Docker Hub repository. Ensure you have permission to push to it.

## 5. Verify the Image

List your local images:

```bash
docker images
```

Visit [Docker Hub](https://hub.docker.com/) and check your repository.

## 6. Pull the Image

Test downloading the published image:

```bash
docker pull your-username/my-app:v1
```

## Complete Workflow

```bash
docker build -t my-app:v1 .
docker login
docker tag my-app:v1 your-username/my-app:v1
docker push your-username/my-app:v1
docker pull your-username/my-app:v1
```

## Important Notes

- Replace `your-username` with your Docker Hub username.
- Create the repository on Docker Hub if needed.
- Never include passwords, access tokens, or secrets in your image.
- Use version tags such as `v1` or `1.0.0` to identify releases.

## Summary

The Docker image publishing workflow is:

**Build → Login → Tag → Push → Pull**

This lets you share Docker images and deploy them on other machines.