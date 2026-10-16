# 🐳 Day 4 — Dockerfile

## 🎯 Objective

Learn Dockerfile instructions and build custom Docker images to package and run applications in containers.

## 📚 Topics Covered

| No. | Topic | Description |
|---|---|---|
| 1 | [Dockerfile Basics](Dockerfile-Basics.md) | Dockerfile structure and image building |
| 2 | [FROM](FROM.md) | Select the base image |
| 3 | [RUN](RUN.md) | Execute commands during image building |
| 4 | [COPY](COPY.md) | Copy files into the image |
| 5 | [ADD](ADD.md) | Copy files and extract supported local archives |
| 6 | [WORKDIR](WORKDIR.md) | Set the working directory |
| 7 | [ENV](ENV.md) | Set environment variables |
| 8 | [EXPOSE](EXPOSE.md) | Document the container port |
| 9 | [CMD](CMD.md) | Define the default command or arguments |
| 10 | [ENTRYPOINT](ENTRYPOINT.md) | Define the main executable |
| 11 | [VOLUME](VOLUME.md) | Declare a mount point for persistent data |
| 12 | [HEALTHCHECK](HEALTHCHECK.md) | Check application health |

## 🛠️ Practical Example

### 1. Create a Project

```bash
mkdir dockerfile-demo
cd dockerfile-demo
```

### 2. Create `index.html`

```html
<h1>Hello from Docker!</h1>
<p>My first custom Docker image.</p>
```

### 3. Create a `Dockerfile`

```dockerfile
FROM nginx:alpine

WORKDIR /usr/share/nginx/html

COPY index.html index.html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

### 4. Build the Image

```bash
docker build -t my-web:v1 .
```

### 5. Run the Container

```bash
docker run -d --name my-web -p 8080:80 my-web:v1
```

### 6. Test the Application

Open the following URL in your browser:

```text
http://localhost:8080
```

If Docker runs on a remote server, use `http://<SERVER-IP>:8080` and allow inbound TCP port `8080` in the server firewall or security group as appropriate.

### 7. Verify and Clean Up

```bash
docker images
docker ps
docker logs my-web
docker rm -f my-web
```

## 🧠 Key Concepts Learned

- Dockerfile syntax and structure
- Base images and image building
- Build-time commands using `RUN`
- Copying application files
- Working directories and environment variables
- Container ports and port publishing
- Difference between `CMD` and `ENTRYPOINT`
- Volumes and persistent data
- Container health checks
- Docker image build best practices

## 📝 Summary

A Dockerfile contains instructions for building a Docker image. By combining a base image, application files, dependencies, and runtime configuration, you can create reproducible images for deploying applications.


