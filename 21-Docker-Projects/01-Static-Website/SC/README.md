# 🐳 Static Website Using Docker

## 📌 Project Overview

This project demonstrates how to build and deploy a static website using Docker and Nginx.

The website is created using HTML and CSS and hosted inside a Docker container using the lightweight Nginx Alpine image.

## 🎯 Objectives

- Understand Dockerfile basics.
- Build a custom Docker image.
- Run a container using Nginx.
- Learn Docker port mapping.
- Deploy a static website inside a container.
- Verify container status and logs.

## 🛠️ Technologies Used

- Docker
- Nginx
- HTML5
- CSS3
- Linux

## 📁 Project Structure

```text
01-Static-Website/
├── README.md
├── Dockerfile
└── website/
    ├── index.html
    └── style.css
```

## 🐳 Dockerfile

```dockerfile
FROM nginx:alpine

COPY website/ /usr/share/nginx/html/

EXPOSE 80
```

## 🚀 Build the Docker Image

```bash
docker build -t my-static-website:v1 .
```

## ▶️ Run the Container

```bash
docker run -d \
  --name static-website \
  -p 8080:80 \
  my-static-website:v1
```

## 🌐 Access the Website

Open the following URL in your browser:

```text
http://localhost:8080
```

For an AWS EC2 deployment, use:

```text
http://YOUR_EC2_PUBLIC_IP:8080
```

Ensure the EC2 security group permits the required inbound traffic.

## 🔍 Verify the Container

Check running containers:

```bash
docker ps
```

View logs:

```bash
docker logs static-website
```

Test the HTTP response:

```bash
curl -I http://localhost:8080
```

## 🛑 Stop the Container

```bash
docker stop static-website
```

## 🗑️ Remove the Container

```bash
docker rm static-website
```

## 🧹 Remove the Docker Image

```bash
docker rmi my-static-website:v1
```

## 📚 Key Learnings

- Docker image creation
- Dockerfile instructions
- Container lifecycle management
- Port mapping
- Nginx web server basics
- Static website deployment

## 🚀 Future Improvements

- Push the image to Docker Hub.
- Deploy the website on AWS EC2.
- Add a custom Docker network.
- Configure HTTPS using a reverse proxy.
- Automate deployment using Jenkins CI/CD.

## 👨‍💻 Author

Docker Learning Journey — Project 01

**Status:** Completed