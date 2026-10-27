# 06 - Docker Registry

## 📌 Overview

Learn how to store, manage, share, and distribute Docker images using Docker Hub and private Docker registries.

## 🎯 Objectives

- Understand Docker registries.
- Learn Docker Hub authentication.
- Push and pull Docker images.
- Understand private registries.
- Implement Docker image tagging strategies.
- Manage image versions effectively.

## 📂 Topics Covered

| File | Description |
|---|---|
| [Docker-Hub.md](./Docker-Hub.md) | Introduction to Docker Hub |
| [Image-Tagging-Strategy.md](./Image-Tagging-Strategy.md) | Manage image versions using tags |
| [Login.md](./Login.md) | Authenticate with Docker registries |
| [Private-Registry.md](./Private-Registry.md) | Work with private Docker registries |
| [Pull-Image.md](./Pull-Image.md) | Download images from a registry |
| [Push-Image.md](./Push-Image.md) | Upload images to Docker Hub |

## 🔄 Docker Registry Workflow

```text
Dockerfile
    |
    v
Build Image
    |
    v
Tag Image
    |
    v
Login to Registry
    |
    v
Push Image
    |
    v
Pull Image
    |
    v
Run Container
```

## 🛠️ Important Commands

### 1. Login

```bash
docker login
```

### 2. Build an Image

```bash
docker build -t my-app:v1 .
```

### 3. Tag an Image

Replace `your-username` with your Docker Hub username.

```bash
docker tag my-app:v1 your-username/my-app:v1
```

### 4. Push an Image

```bash
docker push your-username/my-app:v1
```

### 5. Pull an Image

```bash
docker pull your-username/my-app:v1
```

### 6. Run a Container

```bash
docker run -d --name my-container your-username/my-app:v1
```

### 7. Logout

```bash
docker logout
```

## 🔐 Best Practices

- Use meaningful image tags such as `v1`, `v2`, or `1.0.0`.
- Never upload passwords, access tokens, or secrets to a repository.
- Use private registries for images that require restricted access.
- Apply appropriate access permissions.
- Avoid relying only on the `latest` tag for production deployments.
- Use image digests when you need to identify an exact image version.

## 🧪 Practice Tasks

1. Create a Docker Hub account.
2. Build a Docker image locally.
3. Tag the image with your Docker Hub username.
4. Push the image to Docker Hub.
5. Pull the image and run a container.
6. Practice logging in to and out of a registry.
7. Create different image tags, such as `v1` and `v2`.
8. Explore how private registries control image access.

## 📚 Learning Outcome

After completing this section, you should understand how to publish, download, version, and manage Docker images using container registries.

**Key Workflow:** Build → Tag → Login → Push → Pull → Run