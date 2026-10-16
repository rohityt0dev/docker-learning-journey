# EXPOSE Instruction

`EXPOSE` documents the port on which an application inside the container listens. It does not publish the port to the host.

## Syntax

```dockerfile
EXPOSE port
```

## Example

```dockerfile
FROM nginx:alpine

EXPOSE 80
```

Build and run with port mapping:

```bash
docker build -t my-web .
docker run -d --name my-web -p 8080:80 my-web
```

Access the application at:

```text
http://localhost:8080
```

## Key Point

> `EXPOSE` documents a container port; `-p` publishes a port to the host.