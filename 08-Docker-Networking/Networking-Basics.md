# Docker Networking Basics

## Objective

Understand how Docker containers communicate with each other, the host machine, and external networks.

## 1. What Is Docker Networking?

Docker networking allows containers to communicate with other containers, access external networks, and expose applications to users.

### Why Is Docker Networking Important?

- Enables communication between containers.
- Connects containers to external networks.
- Controls how applications are accessed.
- Supports multi-container applications such as frontend, backend, and database services.

## 2. List Docker Networks

```bash
docker network ls
```

Docker creates several built-in networks, including:

| Network | Description |
|---|---|
| `bridge` | Default network for standalone containers |
| `host` | Uses the host's network namespace on supported Linux systems |
| `none` | Disables normal container networking |

## 3. Inspect a Network

```bash
docker network inspect bridge
```

Displays details about the network, including connected containers and network configuration.

## 4. Run a Container on the Default Bridge

```bash
docker run -d \
  --name my-nginx \
  nginx
```

Check the container's network information:

```bash
docker inspect my-nginx
```

Look for the `NetworkSettings` section.

## 5. Create a Custom Bridge Network

```bash
docker network create my-network
```

Verify it:

```bash
docker network ls
```

Custom bridge networks allow containers to communicate with each other using container names as DNS names.

## 6. Connect Containers to the Same Network

Start two containers:

```bash
docker run -d \
  --name app1 \
  --network my-network \
  nginx
```

```bash
docker run -d \
  --name app2 \
  --network my-network \
  nginx
```

Test name resolution from `app1`:

```bash
docker exec app1 getent hosts app2
```

If name resolution succeeds, Docker resolves `app2` to its container IP address.

## 7. Publish a Container Port

To make an Nginx web server accessible through the host:

```bash
docker run -d \
  --name web-server \
  -p 8080:80 \
  nginx
```

- `8080` — Port on the host.
- `80` — Port inside the container.

Open `http://localhost:8080` on the Docker host to access Nginx.

**Note:** If Docker runs on a remote EC2 instance, use its reachable IP or DNS name and allow the required port in its security group and host firewall.

## 8. View Container Ports

```bash
docker ps
```

Example output:

```text
PORTS
0.0.0.0:8080->80/tcp
```

This indicates that host port `8080` is mapped to container port `80`.

## 9. Disconnect and Remove a Network

Disconnect a container:

```bash
docker network disconnect my-network app1
```

Remove a network when it is no longer needed:

```bash
docker network rm my-network
```

Docker cannot remove a network while containers remain connected to it.

## Important Notes

- Containers on the same custom bridge network can communicate using their names.
- Containers on separate networks generally cannot communicate directly unless connected through an appropriate network or routing setup.
- Publishing a port with `-p` makes a container service accessible through a host port.
- Containers on the same bridge network can often communicate without publishing their ports.
- Avoid exposing databases and internal services publicly unless required.

## Summary

Docker networking enables communication between containers, the host, and external systems.

**Learning path:** Networks → Custom Bridge → Container Communication → Port Mapping → Network Management