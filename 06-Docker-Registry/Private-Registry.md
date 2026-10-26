# Docker Private Registry

## Objective

Learn how to authenticate with and use a private Docker image registry.

## 1. What Is a Private Registry?

A private registry stores Docker images with access restricted to authorized users or systems.

Examples include:

- Docker Hub private repositories
- Amazon Elastic Container Registry (Amazon ECR)
- Azure Container Registry (ACR)
- Self-hosted Docker Registry

## 2. Login to a Registry

For a custom registry:

```bash
docker login registry.example.com
```

For Docker Hub:

```bash
docker login
```

Use the credentials or access token required by your registry.

## 3. Tag an Image

Tag your local image with the registry address:

```bash
docker tag my-app:v1 registry.example.com/my-app:v1
```

## 4. Push an Image

```bash
docker push registry.example.com/my-app:v1
```

You need permission to push to the target repository.

## 5. Pull an Image

On a machine with registry access:

```bash
docker login registry.example.com
docker pull registry.example.com/my-app:v1
```

## 6. Run the Image

```bash
docker run -d --name my-container registry.example.com/my-app:v1
```

Add port mapping if the application needs to be accessed through a host port:

```bash
docker run -d --name my-app -p 8080:80 registry.example.com/my-app:v1
```

## 7. Logout

```bash
docker logout registry.example.com
```

## Important Notes

- Use HTTPS for registry connections.
- Grant users only the permissions they need.
- Never commit passwords or access tokens to GitHub.
- Use specific image tags to identify releases.
- Configure registry authentication and access controls securely.

## Summary

A private Docker registry lets authorized users store, share, push, and pull container images securely.

**Workflow:** Login → Tag → Push → Pull → Run