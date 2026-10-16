# RUN Instruction

`RUN` executes commands **during image building**. It is commonly used to install packages and dependencies.

## Syntax

```dockerfile
RUN command
```

## Example

```dockerfile
FROM ubuntu:24.04

RUN apt-get update && apt-get install -y nginx
```

## Key Point

> `RUN` executes commands while building the image, not when the container starts.