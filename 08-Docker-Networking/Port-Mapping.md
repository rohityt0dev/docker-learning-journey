# Docker Port Mapping

## Objective

Learn how to expose container applications through ports on the host machine using Docker port mapping.

## 1. What Is Port Mapping?

**Port mapping** connects a port on the host machine to a port inside a Docker container.

For example:

```text
Host Port: 8080  →  Container Port: 80
```

This allows you to access an application running inside a container through the host machine.

## 2. Basic Syntax

```bash
docker run -d -p HOST_PORT:CONTAINER_PORT IMAGE
```

- `-d` — Runs the container in the background.
- `-p` — Publishes a container port on the host.
- `HOST_PORT` — Port on the host machine.
- `CONTAINER_PORT` — Port used by the application inside the container.

## 3. Run Nginx with Port Mapping

```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  nginx
```

Open this URL on the Docker host:

```text
http://localhost:8080
```

Docker forwards traffic from host port `8080` to container port `80`.

## 4. View Port Mapping

```bash
docker ps
```

Example output:

```text
CONTAINER ID   IMAGE   PORTS
abc123         nginx   0.0.0.0:8080->80/tcp
```

This means host port `8080` forwards traffic to container port `80`.

## 5. Map Multiple Ports

You can publish multiple ports for one container:

```bash
docker run -d \
  --name my-app \
  -p 8080:80 \
  -p 8443:443 \
  nginx
```

This maps:
- Host port `8080` to container port `80`.
- Host port `8443` to container port `443`.

## 6. Bind to a Specific Host IP

By default, Docker typically publishes ports on all host IPv4 interfaces.

To publish a port only on the host's loopback interface:

```bash
docker run -d \
  --name local-nginx \
  -p 127.0.0.1:8080:80 \
  nginx
```

The service is accessible locally through `127.0.0.1:8080`, but is not published on the host's other network interfaces.

## 7. Use a Different Host Port

If host port `8080` is already in use, choose another available port:

```bash
docker run -d \
  --name web-app \
  -p 9090:80 \
  nginx
```

Access the application at:

```text
http://localhost:9090
```

## 8. Check Published Ports

Display port mappings:

```bash
docker port my-nginx
```

Inspect container networking details:

```bash
docker inspect my-nginx
```

## 9. Stop and Remove the Container

```bash
docker stop my-nginx
docker rm my-nginx
```

## 10. Port Mapping vs Expose

| Feature | `-p` / `--publish` | `EXPOSE` |
|---|---|---|
| Purpose | Publishes a container port on the host | Documents the intended container port |
| Host port mapping | Yes | No |
| Makes the application externally accessible by itself | Publishes the port, subject to network and firewall rules | No |

Example Dockerfile instruction:

```dockerfile
EXPOSE 80
```

Run the image with an actual port mapping:

```bash
docker run -d -p 8080:80 nginx
```

## Important Notes

- The application must listen on the container port you publish.
- Publishing a port does not automatically configure cloud security groups or host firewalls.
- On an EC2 instance, allow the required port in the security group only when external access is needed.
- Avoid publishing internal services, such as databases, to public interfaces unnecessarily.

## Summary

Docker port mapping allows users to access applications running inside containers through host ports.

**Example:** `-p 8080:80` maps host port `8080` to container port `80`.