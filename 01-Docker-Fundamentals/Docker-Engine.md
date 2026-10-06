# Docker Engine

Docker Engine is the **core technology that builds and runs Docker containers**.

It provides the runtime environment and tools required to create, manage, and run containers.

## Docker Engine Architecture

```text
┌─────────────────────────────┐
│        Docker Client        │
│          (Docker CLI)       │
└──────────────┬──────────────┘
               │
          Docker API
               ↓
┌─────────────────────────────┐
│       Docker Daemon         │
│          (dockerd)           │
├─────────────────────────────┤
│  Images │ Containers        │
│  Networks │ Volumes         │
└──────────────┬──────────────┘
               ↓
┌─────────────────────────────┐
│       Container Runtime     │
│          containerd         │
└─────────────────────────────┘
```

## Main Components

### 1. Docker CLI

The Docker CLI is the command-line interface used to interact with Docker Engine.

```bash
docker ps
docker images
docker run nginx
```

### 2. Docker Daemon

The Docker Daemon (`dockerd`) runs in the background and manages Docker resources.

It manages:

- Containers
- Images
- Networks
- Volumes

### 3. Docker API

The Docker API allows the Docker CLI and other applications to communicate with the Docker Daemon.

```text
Docker CLI
    ↓
Docker API
    ↓
Docker Daemon
```

### 4. containerd

`containerd` is a container runtime responsible for managing the container lifecycle.

It handles tasks such as:

- Starting containers
- Stopping containers
- Managing container processes
- Managing container images

### 5. runc

`runc` is a low-level container runtime that creates and runs containers according to OCI standards.

```text
Docker CLI
    ↓
Docker Daemon
    ↓
containerd
    ↓
runc
    ↓
Container
```

## Docker Engine Workflow

When you run:

```bash
docker run nginx
```

The basic flow is:

```text
Docker CLI
    ↓
Docker Daemon
    ↓
Check Image
    ↓
Pull Image if needed
    ↓
containerd
    ↓
runc
    ↓
Container Starts
```
---