# Docker Architecture

Docker uses a **client-server architecture** to build, run, and manage containers.

## Architecture

```text
                 Docker Host
┌─────────────────────────────────────────┐
│                                         │
│  Docker Client                          │
│      │                                  │
│      │ Docker API                       │
│      ↓                                  │
│  Docker Daemon (dockerd)                │
│      │                                  │
│      ├── Images                         │
│      ├── Containers                     │
│      ├── Networks                       │
│      └── Volumes                        │
│                                         │
└─────────────────────────────────────────┘
             │
             ↓
        Docker Registry
        (Docker Hub)
```

## Main Components

### 1. Docker Client

The Docker Client is the command-line interface used to interact with Docker.

Example:

```bash
docker run nginx
docker ps
docker images
```

The client sends commands to the Docker Daemon through the Docker API.

### 2. Docker Daemon

The Docker Daemon (`dockerd`) is responsible for managing Docker objects.

It manages:

- Containers
- Images
- Networks
- Volumes

### 3. Docker Engine

Docker Engine is the core technology that allows you to build and run containers.

It includes:

```text
Docker CLI
    ↓
Docker API
    ↓
Docker Daemon
    ↓
Container Runtime
```

### 4. Docker Images

Images are read-only templates used to create containers.

```text
Dockerfile
    ↓
Docker Image
    ↓
Container
```

### 5. Docker Containers

A container is a running instance of a Docker image.

```bash
docker run nginx
```

This creates and starts a container from the `nginx` image.

### 6. Docker Registry

A registry stores and distributes Docker images.

Examples:

- Docker Hub
- Amazon ECR
- GitHub Container Registry
- Azure Container Registry



## Docker Workflow

```text
Developer
    ↓
Docker CLI
    ↓
Docker Daemon
    ↓
Build / Pull Image
    ↓
Run Container
    ↓
Application
```

---