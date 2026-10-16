# FROM Instruction

`FROM` specifies the base image used to build a Docker image.

## Syntax

```dockerfile
FROM image[:tag]
```

## Example

```dockerfile
FROM ubuntu:24.04
```

Use a specific base image and version to make builds more predictable.

## Key Point

> `FROM` defines the starting point of a Docker image.