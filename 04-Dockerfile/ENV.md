# ENV Instruction

`ENV` sets environment variables that are available to subsequent Dockerfile instructions and containers created from the image.

## Syntax

```dockerfile
ENV KEY=value
```

## Example

```dockerfile
FROM ubuntu:24.04

ENV APP_ENV=production

CMD ["printenv", "APP_ENV"]
```

Build and run:

```bash
docker build -t my-app .
docker run --rm my-app
```

Output:

```text
production
```

## Key Point

> `ENV` defines environment variables. Do not use it to store secrets because values can persist in image metadata.