# Full-Stack Application with Docker Compose

## 🎯 Objective
Learn how to organize a full-stack application into separate services.

## 1. Example Architecture

```text
User
 |
 v
Frontend
 |
 v
Backend API
 |
 v
Database
```

## 2. Example `compose.yaml`

```yaml
services:
  frontend:
    image: nginx:alpine
    ports:
      - "8080:80"

  backend:
    image: your-backend-image
    environment:
      DB_HOST: db
      DB_PORT: "3306"
      DB_NAME: appdb
    depends_on:
      - db

  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password
      MYSQL_DATABASE: appdb
    volumes:
      - db-data:/var/lib/mysql

volumes:
  db-data:
```

## 3. Start the Application

```bash
docker compose up -d
```

## 4. Check Services

```bash
docker compose ps
docker compose logs
```

## 5. Stop the Application

```bash
docker compose down
```

## ✅ Key Points
- Each service has a separate responsibility.
- Compose connects services through its default network.
- Named volumes persist database data.
- Replace placeholder images with compatible application images.
- Configure the frontend to call the backend API and the backend to connect to the database.
- Use secure credentials and health checks for production deployments.