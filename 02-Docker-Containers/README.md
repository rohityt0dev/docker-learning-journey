# 🐳 Day 2 — Docker Images and Containers

## 🎯 Objective

Learn how to create, run, manage, inspect, and troubleshoot Docker containers and understand their lifecycle.

## 📚 Topics Covered

| No. | Topic | Description |
|---|---|---|
| 1 | [Container Basics](Container-Basics.md) | Introduction to containers and essential commands |
| 2 | [Container Lifecycle](Container-Lifecycle.md) | Created, running, paused, stopped, and removed states |
| 3 | [Docker Container Management](Docker-Container-Management.md) | Manage and inspect containers |
| 4 | [Docker Exec](Docker-Exec.md) | Execute commands inside running containers |
| 5 | [Docker Logs](Docker-Logs.md) | View and troubleshoot container logs |
| 6 | [Docker PS](Docker-PS.md) | List and inspect container status |
| 7 | [Docker Run](Docker-Run.md) | Create and start containers with different options |
| 8 | [Docker Start and Stop](Docker-Start-Stop.md) | Start, stop, restart, and terminate containers |

## 🛠️ Practical Commands

### 1. Run a Container

```bash
docker run -d --name my-nginx -p 8080:80 nginx
```

### 2. List Containers

```bash
docker ps
docker ps -a
```

### 3. Manage Containers

```bash
docker stop my-nginx
docker start my-nginx
docker restart my-nginx
```

### 4. View Logs and Execute Commands

```bash
docker logs my-nginx
docker exec my-nginx ls
docker exec -it my-nginx /bin/sh
```

### 5. Inspect and Remove Containers

```bash
docker inspect my-nginx
docker stats my-nginx
docker rm -f my-nginx
```

## 🔄 Container Lifecycle

```text
Docker Image
     ↓
docker create
     ↓
  Created
     ↓
docker start
     ↓
  Running
     ↓
docker stop
     ↓
  Stopped
     ↓
docker rm
     ↓
  Removed
```

## 🧠 Key Concepts Learned

- Docker images and containers
- Container lifecycle and states
- Foreground and detached modes
- Container naming
- Port mapping
- Container logs and interactive shells
- Starting, stopping, restarting, and removing containers
- Inspecting containers and monitoring resource usage
- Difference between `docker run` and `docker start`


## 📝 Summary

Docker containers provide isolated environments for running applications. Docker CLI commands help manage their lifecycle, inspect their status, view logs, execute commands, and expose application ports.

