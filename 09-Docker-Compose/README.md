# 09 - Docker Compose

## 📌 Overview

Learn how to define, configure, and manage multi-container applications using Docker Compose. This section covers Compose configuration files, services, networks, volumes, environment variables, health checks, and essential Docker Compose commands.

## 🎯 Objectives

- Understand Docker Compose fundamentals.
- Learn how to write `compose.yaml` files.
- Run and manage multiple containers using a single configuration.
- Understand Docker Compose services and dependencies.
- Configure environment variables.
- Manage persistent data using volumes.
- Configure networks for service communication.
- Implement health checks.
- Learn essential Docker Compose commands.
- Start, stop, and remove multi-container applications.

## 📂 Topics Covered

| File | Description |
|---|---|
| [Compose-Basics.md](Compose-Basics.md) | Introduction to Docker Compose |
| [Compose-Commands.md](Compose-Commands.md) | Essential Docker Compose commands |
| [compose.yaml](compose.yaml) | Example multi-container application configuration |
| [depends-on.md](depends-on.md) | Configure service startup dependencies |
| [docker-compose-down.md](docker-compose-down.md) | Stop and remove Compose services |
| [docker-compose-up.md](docker-compose-up.md) | Build and start Compose services |
| [Environment-Variables.md](Environment-Variables.md) | Configure services using environment variables |
| [Healthchecks.md](Healthchecks.md) | Monitor service health |
| [Networks.md](Networks.md) | Configure networks for service communication |
| [Services.md](Services.md) | Define and manage application services |
| [Volumes.md](Volumes.md) | Persist application data using volumes |

## 🐳 What Is Docker Compose?

Docker Compose is a tool for defining and managing multi-container applications using a YAML configuration file, usually named `compose.yaml`.

Instead of running multiple `docker run` commands, you can define your application services in one file and manage them together.

## 🔄 Docker Compose Workflow

```text
Create compose.yaml
        |
        v
Define Application Services
        |
        v
Configure Ports, Networks and Volumes
        |
        v
Start Services
        |
        v
Check Containers and Logs
        |
        v
Test Application
        |
        v
Stop and Remove Services
```

## 📝 Example compose.yaml

The following example runs an Nginx web server and an Apache web server.

```yaml
services:
  web:
    image: nginx:latest
    container_name: nginx-web
    ports:
      - "8080:80"
    restart: unless-stopped

  app:
    image: httpd:latest
    container_name: apache-web
    ports:
      - "8081:80"
    restart: unless-stopped
```

### Configuration Explanation

| Configuration | Description |
|---|---|
| `services` | Defines application services |
| `image` | Specifies the Docker image |
| `container_name` | Sets a custom container name |
| `ports` | Maps host ports to container ports |
| `restart` | Defines the container restart policy |
| `unless-stopped` | Restarts the container unless it has been explicitly stopped |

## 🛠️ Important Docker Compose Commands

### 1. Start Services

```bash
docker compose up
```

Run services in the background:

```bash
docker compose up -d
```

### 2. Build and Start Services

```bash
docker compose up -d --build
```

Build images before starting the services.

### 3. Check Running Services

```bash
docker compose ps
```

### 4. View Logs

```bash
docker compose logs
```

Follow logs continuously:

```bash
docker compose logs -f
```

### 5. Stop Services

```bash
docker compose stop
```

Stops containers without removing them.

### 6. Restart Services

```bash
docker compose restart
```

### 7. Execute Commands Inside a Service

```bash
docker compose exec web sh
```

Opens a shell inside the running `web` service container.

### 8. Validate Compose Configuration

```bash
docker compose config
```

Displays the resolved Compose configuration and helps identify configuration errors.

### 9. Pull Images

```bash
docker compose pull
```

Downloads the images specified in the Compose configuration.

### 10. Stop and Remove Services

```bash
docker compose down
```

Stops and removes the project's containers and networks.

**Warning:** To remove associated Compose-managed volumes as well, use `docker compose down --volumes`. This can permanently delete stored data.

## 🔗 Important Docker Compose Concepts

| Concept | Purpose |
|---|---|
| Services | Define application components |
| Ports | Publish container ports on the host |
| Networks | Enable communication between services |
| Volumes | Persist data beyond container removal |
| Environment Variables | Configure applications |
| Depends On | Define service startup dependencies |
| Health Checks | Report whether a service is healthy |
| Restart Policies | Control when containers restart |

## 🔐 Best Practices

- Keep the Compose configuration organized and readable.
- Use meaningful service names.
- Use specific image versions instead of relying entirely on `latest`.
- Store environment-specific configuration in appropriate environment files.
- Never commit passwords, API keys, or other secrets to GitHub.
- Use named volumes for important persistent data.
- Configure health checks for applications that need readiness monitoring.
- Use `depends_on` appropriately and remember that basic dependency ordering does not guarantee application readiness.
- Avoid publishing internal services unnecessarily.
- Validate configuration using `docker compose config`.
- Review volume deletion commands before running them.

## 📚 Learning Outcomes

After completing this section, you should understand how to configure, start, monitor, and manage multi-container applications using Docker Compose.

You will be able to define application services, configure networking and persistent storage, manage environment variables, and troubleshoot common Compose issues.

**Key Workflow:** Define → Configure → Start → Monitor → Troubleshoot → Stop and Remove