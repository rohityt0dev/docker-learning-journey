# 07 - Docker Storage

## 📌 Overview

Learn how Docker manages container filesystems and persistent storage using Docker volumes and bind mounts. Understand how to store, access, back up, and manage data throughout the container lifecycle.

## 🎯 Objectives

- Understand the Docker container filesystem.
- Learn the difference between image layers and container writable layers.
- Understand Docker volumes and their benefits.
- Create, inspect, and manage Docker volumes.
- Learn how to use bind mounts to share files between the host and containers.
- Understand how to preserve data when containers are removed.
- Learn basic Docker storage management and backup commands.
- Apply storage best practices for containerized applications.

## 📂 Topics Covered

| File | Description |
|---|---|
| [Bind-Mounts.md](Bind-Mounts.md) | Share files and directories between the host and containers |
| [Container-Filesystem.md](Container-Filesystem.md) | Understand container filesystems, image layers, and writable layers |
| [Volume-Commands.md](Volume-Commands.md) | Create, inspect, back up, and remove Docker volumes |
| [Volumes.md](Volumes.md) | Learn Docker volumes and persistent container storage |

## 🗂️ Docker Storage Architecture

```text
                 Docker Container
                        |
           +------------+------------+
           |                         |
           v                         v
    Image Read-Only Layer      Writable Layer
           |                         |
           v                         v
    Base Image Files          Runtime Changes
           |
           v
    Application Files

           Persistent Storage
                  |
          +-------+-------+
          |               |
          v               v
    Docker Volumes    Bind Mounts
          |               |
          v               v
    Docker-Managed    Host Files and
       Storage         Directories
```

**Key Points:**

- **Image layers:** Read-only filesystem layers used to create containers.
- **Writable layer:** Stores changes made inside a container that are not written to mounted storage.
- **Docker volumes:** Store data independently of a container's lifecycle.
- **Bind mounts:** Connect specific host files or directories to paths inside containers.


## 🛠️ Important Commands

### 1. List Docker Volumes

Display all Docker volumes:

```bash
docker volume ls
```

### 2. Create a Volume

```bash
docker volume create my-data
```

### 3. Inspect a Volume

```bash
docker volume inspect my-data
```

### 4. Run a Container with a Volume

```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  -v my-data:/usr/share/nginx/html \
  nginx
```

**Key Takeaway**: Docker volumes and bind mounts allow you to manage data independently of a container's writable layer.

**Key Workflow**: Create Storage → Mount Storage → Read and Write Data → Verify Persistence → Back Up Data → Manage Storage