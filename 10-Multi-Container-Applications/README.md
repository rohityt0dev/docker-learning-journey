# 10 - Multi-Container Applications

## 📌 Overview

Learn how to build, configure, and manage multi-container applications using Docker and Docker Compose. This section covers communication between frontend, backend, web servers, and databases.

## 🎯 Objectives

- Understand multi-container application architecture.
- Learn frontend and backend communication.
- Connect backend applications with databases.
- Configure Nginx as a reverse proxy.
- Deploy web applications with MySQL.
- Integrate phpMyAdmin with MySQL.
- Understand Docker Compose service dependencies.
- Configure networks and persistent volumes.
- Build and manage full-stack applications.

## 📂 Topics Covered

| File | Description |
|---|---|
| [Web-and-Database.md](Web-and-Database.md) | Connect web applications with MySQL using phpMyAdmin |
| [Frontend-Backend.md](Frontend-Backend.md) | Understand frontend and backend communication |
| [Backend-Database.md](Backend-Database.md) | Connect backend services with databases |
| [Nginx-App.md](Nginx-App.md) | Configure Nginx as a reverse proxy |
| [Full-Stack-Application.md](Full-Stack-Application.md) | Build a complete multi-container application |

## 🏗️ Multi-Container Architecture

A multi-container application separates different components into independent services.

```text
                  User
                    |
                    v
               Nginx Frontend
                    |
                    v
                Backend
                    |
                    v
                 MySQL
                    |
                    v
               Database

             phpMyAdmin
                    |
                    v
                  MySQL
```

## 🐳 Docker Compose Example

The following example demonstrates a multi-container application containing Nginx, Apache, MySQL, and phpMyAdmin.

```yaml
services:

  nginx:
    image: nginx:alpine
    container_name: frontend
    ports:
      - "8080:80"
    volumes:
      - ./nginx.conf:/etc/nginx/conf.d/default.conf:ro
    depends_on:
      - backend

  backend:
    image: httpd:alpine
    container_name: backend
    expose:
      - "80"

  db:
    image: mysql:8
    container_name: mysql-db
    environment:
      MYSQL_ROOT_PASSWORD: example-password
      MYSQL_DATABASE: appdb
    volumes:
      - db-data:/var/lib/mysql

  phpmyadmin:
    image: phpmyadmin:latest
    container_name: phpmyadmin
    ports:
      - "8081:80"
    environment:
      PMA_HOST: db
    depends_on:
      - db

volumes:
  db-data:
```

**Note:** This is a learning setup. The Apache backend is not automatically connected to MySQL. Actual application integration requires backend code and database configuration.

## 🔄 Application Workflow

```text
          Docker Compose
                 |
                 v
          Start Services
                 |
       +---------+---------+
       |         |         |
       v         v         v
     Nginx     Backend    MySQL
       |         |         |
       |         |         |
       +---------+         |
                 |         |
                 v         v
           Application   phpMyAdmin
           Communication   |
                           v
                       Database
```

## 🛠️ Important Docker Compose Commands

### 1. Start All Services

```bash
docker compose up -d
```

### 2. Check Running Services

```bash
docker compose ps
```

### 3. View Logs

```bash
docker compose logs
```

### 4. Follow Live Logs

```bash
docker compose logs -f
```

### 5. Restart Services

```bash
docker compose restart
```

### 6. Access Nginx Container

```bash
docker compose exec nginx sh
```

### 7. Access Backend Container

```bash
docker compose exec backend sh
```

### 8. Access MySQL Container

```bash
docker compose exec db bash
```

### 9. Rebuild and Start Services

```bash
docker compose up -d --build
```

### 10. Stop and Remove Services

```bash
docker compose down
```

### 11. Remove Services and Volumes

```bash
docker compose down -v
```

**Warning:** This removes the Compose-managed database volume and its stored data.

## 🌐 Application Access

After starting the services, access them through:

| Service | URL |
|---|---|
| Nginx Frontend | http://localhost:8080 |
| phpMyAdmin | http://localhost:8081 |
| Backend | Internal Docker network |

For EC2 deployments, replace `localhost` with your EC2 public IP and configure the required security group rules.

## 🔑 Important Concepts

| Concept | Description |
|---|---|
| Multi-Container Application | Application divided into multiple services |
| Frontend | Handles user interface |
| Backend | Handles application logic |
| Nginx | Web server and reverse proxy |
| Apache | Web server |
| MySQL | Relational database |
| phpMyAdmin | Web-based MySQL management tool |
| Docker Networks | Enable communication between containers |
| Docker Volumes | Provide persistent storage |
| Depends On | Defines service startup dependencies |

## 🔐 Best Practices

- Separate application components into individual containers.
- Use Docker Compose to manage multiple services.
- Use service names for container-to-container communication.
- Use named volumes for database persistence.
- Store credentials using environment variables or secrets.
- Never commit real passwords to GitHub.
- Configure health checks for important services.
- Avoid exposing database ports publicly.
- Use specific image versions instead of relying only on `latest`.
- Configure proper application connection settings.
- Test service communication before deployment.

## 🧪 Practice Tasks

1. Create a Docker Compose project with Nginx and Apache.
2. Configure Nginx as a reverse proxy.
3. Run MySQL using Docker Compose.
4. Connect phpMyAdmin to MySQL.
5. Create a named volume for database persistence.
6. Connect frontend and backend services.
7. Configure backend database connectivity.
8. Practice accessing containers using `docker compose exec`.
9. Monitor services using Docker Compose logs.
10. Build a complete multi-container application.

## 📚 Learning Outcomes

After completing this section, you should understand how to create, configure, connect, and manage multiple Docker containers using Docker Compose.

You will gain practical experience with frontend, backend, Nginx, Apache, MySQL, phpMyAdmin, Docker networks, and persistent volumes.

**Key Workflow:** Frontend → Backend → Database → Docker Compose → Multi-Container Deployment