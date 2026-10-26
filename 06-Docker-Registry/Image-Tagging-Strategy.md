# Docker Image Tagging Strategy

## Objective

Learn how to create consistent Docker image tags for development, testing, and production.

## 1. What Is an Image Tagging Strategy?

An image tagging strategy defines how Docker images are named and versioned so teams can identify releases and deploy the correct version.

## 2. Common Tagging Strategies

### Version Tags

```text
my-app:1.0.0
my-app:1.1.0
my-app:2.0.0
```

Use version tags to identify application releases.

### Environment Tags

```text
my-app:dev
my-app:staging
my-app:prod
```

These identify intended environments, but tags can be moved to different images. Use immutable release identifiers for reliable deployments.

### Git Commit Tags

```text
my-app:a1b2c3d
```

A commit-based tag helps identify the source code used to build an image.

### Latest Tag

```text
my-app:latest
```

`latest` is a conventional tag, not a guarantee that the image is the newest version.

## 3. Build and Tag an Image

```bash
docker build -t my-app:1.0.0 .
```

Add a Git commit-based tag:

```bash
docker tag my-app:1.0.0 my-app:a1b2c3d
```

## 4. Push Versioned Images

```bash
docker tag my-app:1.0.0 username/my-app:1.0.0
docker push username/my-app:1.0.0
```

Replace `username` with your Docker Hub username.

## 5. Best Practices

- Use semantic versioning, such as `1.2.3`.
- Include a Git commit identifier when useful for traceability.
- Avoid relying only on `latest` for production deployments.
- Do not reuse release tags for different image contents.
- Consider deploying by image digest when exact image identity is required.
- Apply a consistent tagging convention across environments.

## Summary

A good Docker image tagging strategy improves version control, traceability, and deployment reliability.

**Recommended approach:** Use release versions such as `1.2.3`, optionally add a Git commit tag, and use image digests when you need to guarantee the exact image deployed.