# Docker Build Context

## Objective
Understand the Docker build context and how Docker uses files when building an image.

## What Is Build Context?

The **build context** is the set of files and directories Docker can access during an image build.

When you run:

```bash
docker build -t my-app:v1 .
```

## Summary

The build context determines which files Docker can access during an image build. Keep it small and use `.dockerignore` to improve build efficiency.