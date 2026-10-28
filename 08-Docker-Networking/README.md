# 08 - Docker Networking

## 📌 Overview

Learn how Docker networking works and how containers communicate with each other, the host machine, and external networks. This section covers network fundamentals, port mapping, custom networks, container communication, and network troubleshooting.

## 🎯 Objectives

- Understand Docker networking fundamentals.
- Learn about Docker network drivers.
- Create and manage custom Docker networks.
- Enable communication between containers.
- Understand Docker port mapping.
- Configure container networking using container names.
- Inspect and troubleshoot Docker networks.
- Learn how to expose applications running inside containers.

## 📂 Topics Covered

| File | Description |
|---|---|
| [Networking-Basics.md](Networking-Basics.md) | Introduction to Docker networking |
| [Port-Mapping.md](Port-Mapping.md) | Publish container ports on the host machine |
| [Container-Communication.md](Container-Communication.md) | Enable communication between containers |
| [Custom-Network.md](Custom-Network.md) | Create and manage custom Docker networks |
| [Network-Troubleshooting.md](Network-Troubleshooting.md) | Diagnose and resolve common networking problems |

## 🌐 Docker Networking Overview

Docker networking allows containers to communicate with each other and connect to external systems.

## 🔄 Docker Networking Workflow

```text
Create Docker Network
         |
         v
Run Containers
         |
         v
Connect Containers to Network
         |
         v 
Enable Container-to-Container Communication
         |
         v
Publish Ports When Host Access Is Required
         |
         v
Inspect and Troubleshoot Network
```

## 🛠️ Important Docker Networking Commands

### 1. List Docker Networks

```bash
docker network ls
```

Displays the available Docker networks.

### 2. Create a Custom Network

```bash
docker network create app-network
```

Creates a custom bridge network named `app-network`.

### 3. Inspect a Network

```bash
docker network inspect app-network
```

Displays network configuration and connected containers.

### 4. Run a Container on a Network

```bash
docker run -d \
  --name app1 \
  --network app-network \
  nginx
```

Starts an Nginx container connected to `app-network`.

### 5. Run a Second Container

```bash
docker run -d \
  --name app2 \
  --network app-network \
  nginx
```

Starts another Nginx container on the same network.

### 6. Test Container Name Resolution

```bash
docker exec app1 getent hosts app2
```

Checks whether `app1` can resolve the name `app2`.

Both containers must be connected to the same suitable user-defined network.

### 7. Publish a Container Port

```bash
docker run -d \
  --name web-server \
  -p 8080:80 \
  nginx
```

Maps host port `8080` to container port `80`.

Access the application locally at:

```text
http://localhost:8080
```

### 8. View Container Port Mappings

```bash
docker port web-server
```

Displays the published ports for the container.

### 9. Connect an Existing Container

```bash
docker network connect app-network my-container
```

Connects an existing container to the specified network.

### 10. Disconnect a Container

```bash
docker network disconnect app-network my-container
```

Disconnects a container from the network.

### 11. Remove a Network

```bash
docker network rm app-network
```

Removes the network when no containers remain connected to it.

## 🔗 Container Communication Example

Create a custom network:

```bash
docker network create app-network
```

Start two containers:

```bash
docker run -d --name app1 --network app-network nginx

docker run -d --name app2 --network app-network nginx
```

Test DNS resolution:

```bash
docker exec app1 getent hosts app2
```

Test HTTP communication from another temporary container:

```bash
docker run --rm \
  --network app-network \
  curlimages/curl:latest \
  http://app2
```

The request should return the default Nginx welcome page if the containers are running correctly and network communication is working.

Clean up:

```bash
docker rm -f app1 app2

docker network rm app-network
```

## 🔌 Port Mapping vs Container Communication

| Feature | Container Communication | Port Mapping |
|---|---|---|
| Purpose | Allows containers to communicate | Allows access through a host port |
| Typical use | Backend communicating with a database | Users accessing a web application |
| Docker configuration | Shared network | `-p HOST_PORT:CONTAINER_PORT` |
| Requires published ports? | No, for communication over the same suitable Docker network | Yes, when publishing a container port |
| Example | `http://app2:80` | `http://localhost:8080` |

## 🔐 Best Practices

- Use custom bridge networks for standalone multi-container applications.
- Use container names instead of hardcoding container IP addresses.
- Avoid publishing ports that do not need external access.
- Keep databases and internal services off public interfaces unless necessary.
- Inspect networks before changing their configurations.
- Check container logs when applications cannot communicate.
- Verify that applications listen on the expected container ports.
- Configure cloud security groups and host firewalls when remote access is required.
- Disconnect unused containers from networks.
- Use appropriate network isolation for different application components.

## 📚 Learning Outcomes

After completing this section, you should understand how Docker networking works, how to connect containers, how to publish application ports, and how to diagnose common networking issues.

**Key Workflow:** Create Network → Run Containers → Connect Services → Test Communication → Publish Ports When Needed → Troubleshoot