# Push Docker Image to Docker Hub

Docker Hub is a registry used to store and share Docker images.

## Step 1 — Tag the Image

```bash
docker tag my-app:v1 username/my-app:v1
```

Replace `username` with your Docker Hub username.

## Step 2 — Log In to Docker Hub

```bash
docker login
```

Enter your Docker Hub credentials when prompted.

## Step 3 — Push the Image

```bash
docker push username/my-app:v1
```

## Step 4 — Verify the Image

Visit [Docker Hub](https://hub.docker.com/) and check your repository to confirm that the image was uploaded.

### Key Point

> **`docker tag` prepares the image name, `docker login` authenticates you, and `docker push` uploads the image to Docker Hub.**