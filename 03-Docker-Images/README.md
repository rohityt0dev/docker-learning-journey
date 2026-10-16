# 🐳 Day 3 — Docker Images

## 🎯 Objective

Understand Docker images, image layers, image commands, and how to tag and push images to Docker Hub.

## 📚 Topics Covered

| No. | Topic | Description |
|---|---|---|
| 1 | [What Is a Docker Image?](What-is-Docker-Image.md) | Image fundamentals, naming, tags, and containers |
| 2 | [Docker Image Commands](Image-Commands.md) | Pull, list, inspect, build, tag, and remove images |
| 3 | [Docker Image Layers](Image-Layers.md) | Layers, caching, reuse, and optimization |
| 4 | [Push Docker Image](Docker-Push-Image.md) | Tag, authenticate, and push images to Docker Hub |

## 🛠️ Practical Commands

### 1. List and Download Images

```bash
docker images
docker pull nginx
docker image ls
```

### 2. Inspect Images

```bash
docker image inspect nginx
docker image history nginx
```

### 3. Build an Image

```bash
docker build -t my-app:v1 .
```

### 4. Tag an Image

```bash
docker tag my-app:v1 username/my-app:v1
```

Replace `username` with your Docker Hub username.

### 5. Push an Image to Docker Hub

```bash
docker login
docker push username/my-app:v1
```

### 6. Remove Images

```bash
docker rmi my-app:v1
docker image prune
```

Review the images and containers that depend on an image before removing it.

## 🔄 Docker Image Workflow

```text
      Dockerfile
          ↓
     docker build
          ↓
     Docker Image
          ↓
       docker tag
          ↓
      docker login
          ↓
      docker push
          ↓
      Docker Hub
          ↓
     docker pull
          ↓
    Docker Container
```

## 🧠 Key Concepts Learned

- Docker images and containers
- Image names, tags, and registries
- Downloading and inspecting images
- Building custom images
- Image layers and build caching
- Image tagging and versioning
- Pushing images to Docker Hub
- Removing unused images
- Image optimization best practices



## 📝 Summary

Docker images are read-only templates used to create containers. Images consist of reusable filesystem layers, and Docker provides commands to build, inspect, tag, distribute, and manage them.

Docker Hub allows you to store and share images so they can be pulled and deployed in other environments.

## 🚀 Next Step


