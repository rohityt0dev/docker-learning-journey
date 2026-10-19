# Docker Image Tagging

## Objective
Learn how to tag Docker images to identify and manage different versions.

## What Is Image Tagging?

An image tag is a label used to identify a specific version of a Docker image.

**Syntax:**

```bash
docker build -t image-name:tag .
```

Example:

```bash
docker build -t my-app:v1 .
```

Here:
- `my-app` — Image name
- `v1` — Image tag

.

## Summary

Docker image tagging helps organize image versions and prepare images for sharing through registries such as Docker Hub.