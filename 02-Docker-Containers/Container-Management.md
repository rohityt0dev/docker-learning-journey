# Docker Container Management

Docker provides commands to create, view, start, stop, restart, inspect, and remove containers.

---

## 📌 List Containers

Show running containers:

```bash
docker ps
```

Show all containers:

```bash
docker ps -a
```

---

## ▶️ Start a Container

```bash
docker start <container>
```

Example:

```bash
docker start my-nginx
```

---

## ⏹️ Stop a Container

```bash
docker stop <container>
```

Example:

```bash
docker stop my-nginx
```

---

## 🔄 Restart a Container

```bash
docker restart <container>
```

---

## 🗑️ Remove a Container

Remove a stopped container:

```bash
docker rm <container>
```

Force remove a running container:

```bash
docker rm -f <container>
```

---

## 📋 View Container Details

```bash
docker inspect <container>
```

Example:

```bash
docker inspect my-nginx
```

---

## 📜 View Container Logs

```bash
docker logs <container>
```

Follow live logs:

```bash
docker logs -f <container>
```

---

## 💻 Execute Commands

Open a shell inside a running container:

```bash
docker exec -it <container> /bin/bash
```

If Bash is unavailable:

```bash
docker exec -it <container> /bin/sh
```

---

## 📊 View Resource Usage

```bash
docker stats
```

For a specific container:

```bash
docker stats my-nginx
```

---

## 🧹 Remove All Stopped Containers

```bash
docker container prune
```

> ⚠️ This removes all stopped containers.

---

## 🔍 Useful Container Commands

| Command | Purpose |
|---|---|
| `docker ps` | List running containers |
| `docker ps -a` | List all containers |
| `docker start` | Start a stopped container |
| `docker stop` | Stop a container |
| `docker restart` | Restart a container |
| `docker rm` | Remove a container |
| `docker inspect` | View container details |
| `docker logs` | View container logs |
| `docker exec` | Execute commands inside container |
| `docker stats` | View resource usage |
| `docker container prune` | Remove stopped containers |

---

---

## 🎯 Key Takeaways

- `docker ps` → View containers
- `docker start` → Start container
- `docker stop` → Stop container
- `docker restart` → Restart container
- `docker rm` → Remove container
- `docker logs` → Check logs
- `docker exec` → Run commands inside
- `docker inspect` → View detailed information
- `docker stats` → Monitor resources