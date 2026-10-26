# Docker Login

## Objective

Learn how to log in to a Docker registry, such as Docker Hub, using the Docker CLI.

## 1. Login to Docker Hub

```bash
docker login
```

Enter your Docker Hub username and authenticate using the method prompted by Docker.

## 2. Login with a Username

```bash
docker login --username your-username
```

Replace `your-username` with your Docker Hub username.

## 3. Login Using an Access Token

For command-line authentication, you can use a Docker Hub personal access token instead of your account password.

```bash
echo "YOUR_ACCESS_TOKEN" | docker login --username your-username --password-stdin
```

Avoid putting real tokens directly into shell commands or scripts, because they may be exposed through shell history or process handling. For safer use, read the token through a secure prompt or secret manager.

## 4. Verify Authentication

After successful login, Docker displays a confirmation message.

You can then push an image:

```bash
docker push your-username/my-app:v1
```

You must have permission to push to the target repository.

## 5. Logout

```bash
docker logout
```

This logs you out of the default Docker registry.

To log out of a specific registry:

```bash
docker logout registry.example.com
```

## Important Notes

- Never commit passwords or access tokens to GitHub.
- Use personal access tokens when appropriate.
- Protect credentials on shared servers.
- Log out when finished on a shared machine.

## Summary

The `docker login` command authenticates the Docker CLI with a registry so you can access private images or push images when authorized.