# WORKDIR Instruction

`WORKDIR` sets the working directory for subsequent Dockerfile instructions, including `RUN`, `CMD`, `ENTRYPOINT`, `COPY`, and `ADD`.

## Syntax

```dockerfile
WORKDIR /path
```

## Example

```dockerfile
FROM ubuntu:24.04

WORKDIR /app

COPY app.py .
```

The file is copied to `/app/app.py`.

## Key Point

> `WORKDIR` sets the working directory and creates it if necessary.