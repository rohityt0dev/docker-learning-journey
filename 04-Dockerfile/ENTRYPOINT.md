# ENTRYPOINT Instruction

`ENTRYPOINT` configures the main executable that runs when a container starts.

## Syntax

```dockerfile
ENTRYPOINT ["executable", "argument"]
```

## Example

```dockerfile
FROM ubuntu:24.04

ENTRYPOINT ["echo"]
CMD ["Hello Docker"]
```

Build and run:

```bash
docker build -t my-app .
docker run --rm my-app
docker run --rm my-app "Hello World"
```

The second run passes `Hello World` as an argument to `echo`.

## Key Point

> `ENTRYPOINT` defines the main executable, while `CMD` can provide default arguments.