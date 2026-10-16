# Day 1 — Docker Fundamentals 🐳

## 🎯 Objective

Learn the basics of Docker, understand its architecture, explore Docker commands, and install Docker on Linux.

## 📚 Topics Covered

| No. | Topic | Description |
|---|---|---|
| 1 | [What is Docker?](What-is-Docker.md) | Introduction, benefits, and key concepts |
| 2 | [Docker Architecture](Docker-Architecture.md) | Client-server architecture and components |
| 3 | [Docker CLI](Docker-CLI.md) | Essential commands for managing Docker |
| 4 | [Docker Engine](Docker-Engine.md) | Docker daemon, API, containerd, and runc |
| 5 | [Docker Installation](Docker-Installation.md) | Install and configure Docker on Linux |
| 6 | [Docker vs VM](Docker-vs-VM.md) | Differences between containers and virtual machines |

## 🛠️ Practical Commands

```bash
# Check Docker version
docker --version

# Display Docker system information
docker info

# Download an image
docker pull nginx

# List Docker images
docker images

# Run a container
docker run -d --name my-nginx -p 8080:80 nginx

# List running containers
docker ps

# View container logs
docker logs my-nginx

# Stop the container
docker stop my-nginx

# Remove the container
docker rm my-nginx
```


## 🧠 Key Concepts Learned

- Docker and containerization
- Docker images and containers
- Docker client-server architecture
- Docker CLI and Docker Engine
- Docker daemon, containerd, and runc
- Docker image registries
- Container port mapping
- Docker installation and service management
- Containers vs virtual machines


## 📝 Summary

Docker is a containerization platform that packages applications and their dependencies into images and runs them in isolated containers.

Understanding these fundamentals prepares you for the next stage: working with Docker images, containers, and Dockerfiles.

---

**Next:** Day 2 — Docker Images and Containers 🚀
