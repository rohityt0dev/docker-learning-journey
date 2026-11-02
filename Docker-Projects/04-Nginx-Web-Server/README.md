
# Nginx Web Server using Docker

## Project Overview

This project demonstrates how to build and run a custom Nginx web server using Docker.

A custom Docker image is created using a Dockerfile, and Nginx is configured using a custom nginx.conf file.

## Technologies Used

- Docker
- Dockerfile
- Nginx
- HTML
- Linux

## Project Structure

```text
02-Nginx-Web-Server/
├── README.md
├── Dockerfile
├── nginx.conf
└── html/
    └── index.html
```

## Features

- Custom Nginx Docker image
- Custom Nginx configuration
- Static website hosting
- Port mapping
- Container management

## Build Docker Image

```bash
docker build -t custom-nginx:v1 .
```

## Run Container

```bash
docker run -d \
  --name nginx-web \
  -p 8080:80 \
  custom-nginx:v1
```

## Access Website

Open your browser:

http://localhost:8080

## Verify Container

```bash
docker ps
```

## View Container Logs

```bash
docker logs nginx-web
```

## Enter Container

```bash
docker exec -it nginx-web sh
```

## Stop Container

```bash
docker stop nginx-web
```

## Start Container

```bash
docker start nginx-web
```

## Remove Container

```bash
docker rm -f nginx-web
```

## Remove Docker Image

```bash
docker rmi custom-nginx:v1
```

## Learning Outcomes

- Understand Nginx web server.
- Create a custom Docker image.
- Configure Nginx using nginx.conf.
- Host a static website inside a container.
- Understand Docker port mapping.
