# Docker Hub

## Objective

Learn how to upload, download, and manage Docker images using Docker Hub.

## What Is Docker Hub?

Docker Hub is a cloud-based registry where you can store, share, and download Docker images.

Website: https://hub.docker.com/

## 1. Login to Docker Hub

```bash
docker login
```

Enter your Docker Hub credentials when prompted.

## 2. Build a Docker Image

```bash
docker build -t my-app:v1 .
```

## 3. Tag the Image

Replace `username` with your Docker Hub username.

```bash
docker tag my-app:v1 username/my-app:v1
```

## 4. Push the Image

Upload your image to Docker Hub:

```bash
docker push username/my-app:v1
```

You can find the image in your Docker Hub repository.

## 5. Pull an Image

Download an image from Docker Hub:

```bash
docker pull username/my-app:v1
```

## 6. Run the Image

```bash
docker run -d --name my-container -p 8080:80 username/my-app:v1
```

Check the container:

```bash
docker ps
```

## 7. Logout

```bash
docker logout
```

## Important Notes

- Create a repository on Docker Hub or use a repository name that Docker Hub allows you to create.
- Use the format `username/image-name:tag`.
- Never upload passwords, API keys, or other secrets inside an image.
- Use specific image tags such as `v1` or `1.0.0`.
- Public repositories can be pulled by others; private repositories require appropriate access.

## Summary

Docker Hub helps developers store, share, and distribute Docker images. The main workflow is **Build → Tag → Push → Pull → Run**.