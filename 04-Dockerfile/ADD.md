# ADD Instruction

`ADD` copies files into an image and can automatically extract supported local tar archives.

## Syntax

```dockerfile
ADD source destination
```

## Example

```dockerfile
FROM ubuntu:24.04

ADD app.tar.gz /app/
```

Docker extracts the supported local tar archive into `/app/`.

## COPY vs ADD

| `COPY` | `ADD` |
|---|---|
| Copies files and directories | Copies files and directories |
| Simple, explicit behavior | Can extract local tar archives |
| Preferred for ordinary file copying | Use when its extra features are needed |

## Key Point

> Prefer `COPY` for ordinary file copying and use `ADD` when you need its additional behavior.