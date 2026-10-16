# COPY Instruction

`COPY` copies files or directories from the build context into the image.

## Syntax

```dockerfile
COPY source destination
```

## Example

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html
```

Build:

```bash
docker build -t my-web:v1 .
```

## Key Point

> Use `COPY` to add application files to a Docker image.