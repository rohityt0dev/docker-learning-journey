# CMD Instruction

`CMD` specifies the default command or arguments when a container starts. It can be overridden when running the container.

## Syntax

```dockerfile
CMD ["executable", "argument"]
```

## Example

```dockerfile
FROM ubuntu:24.04

CMD ["echo", "Hello Docker"]
```

Run:

```bash
docker build -t my-app .
docker run --rm my-app
```

Output:

```text
Hello Docker
```

## Key Point

> `CMD` provides the default runtime command or arguments for a container.