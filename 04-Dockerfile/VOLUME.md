# VOLUME Instruction

`VOLUME` declares a mount point intended for persistent or externally managed data.

## Syntax

```dockerfile
VOLUME ["/path"]
```

## Example

```dockerfile
FROM ubuntu:24.04

VOLUME ["/data"]

CMD ["sleep", "infinity"]
```

Build and run:

```bash
docker build -t my-app .
docker run -d --name my-app my-app
```

For explicitly managed persistent data, use a named volume:

```bash
docker volume create app-data
docker run -d --name my-app -v app-data:/data my-app
```

## Key Point

> `VOLUME` declares a mount point; use Docker volumes to manage persistent container data.