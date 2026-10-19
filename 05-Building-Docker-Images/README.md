# 🐳 Day 5 — Building Docker Images

## 🎯 Objective

Learn how to build Docker images, understand the build context, exclude unnecessary files using `.dockerignore`, and manage image versions using tags.

## 📚 Topics Covered

| No. | Topic | Description |
|---|---|---|
| 1 | [.dockerignore](.dockerignore) | Exclude unnecessary files from the build context |
| 2 | [Docker Build Command](docker-build.md) | Build images using a Dockerfile |
| 3 | [Build Context](Build-Context.md) | Understand which files Docker can access during a build |
| 4 | [Image Tagging](Image-Tagging.md) | Name and version Docker images |

## 🛠️ Practical Commands

### 1. Build a Docker Image

```bash
docker build -t my-app:v1 .
```

- `docker build` — Builds a Docker image.
- `-t` — Assigns an image name and tag.
- `.` — Specifies the current directory as the build context.

### 2. List Images

```bash
docker images
```

### 3. Build Using a Different Dockerfile

```bash
docker build -f Dockerfile.dev -t my-app:dev .
```

### 4. Tag an Existing Image

```bash
docker tag my-app:v1 my-app:v2
```

### 5. Run a Container

```bash
docker run -d --name my-container -p 8080:80 my-app:v1
```

### 6. Verify the Container

```bash
docker ps
docker logs my-container
```

Open `http://localhost:8080` if the image runs a web server listening on container port 80.

## 📁 Docker Build Workflow

```text
      Dockerfile
          +
     Build Context
          +
     .dockerignore
          ↓
     docker build
          ↓
      Docker Image
          ↓
      Image Tagging
          ↓
       Container
```

## 🧠 Key Concepts Learned

- Docker image building
- Dockerfile and build context
- `.dockerignore` patterns
- Docker build command options
- Image names and tags
- Building with custom Dockerfiles
- Running containers from custom images
- Image version management
- Docker build best practices

## 📝 Summary

Docker image building converts a Dockerfile and its build context into a Docker image. The `.dockerignore` file helps exclude unnecessary files, while image tags help identify and manage different versions.

Keeping the build context small and organizing image versions properly makes your Docker workflow more efficient.


