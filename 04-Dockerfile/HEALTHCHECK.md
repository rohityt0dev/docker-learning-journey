# HEALTHCHECK Instruction

`HEALTHCHECK` defines a command Docker uses to check whether a container's application is healthy.

## Syntax

```dockerfile
HEALTHCHECK [OPTIONS] CMD command
```

## Example

```dockerfile
FROM nginx:alpine

EXPOSE 80

HEALTHCHECK --interval=30s --timeout=3s --retries=3 \
  CMD wget -q -O /dev/null http://127.0.0.1/ || exit 1
```

Build and run:

```bash
docker build -t my-web .
docker run -d --name my-web my-web
```

Check health status:

```bash
docker ps
docker inspect --format='{{.State.Health.Status}}' my-web
```

Possible statuses include `starting`, `healthy`, and `unhealthy`.

## Key Point

> `HEALTHCHECK` monitors application health; it does not automatically restart an unhealthy container.