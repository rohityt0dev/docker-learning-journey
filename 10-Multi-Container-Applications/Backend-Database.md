# Backend and Database with Docker

## 🎯 Objective
Learn how a backend service connects to a database.

## 1. Example `compose.yaml`

```yaml
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password
      MYSQL_DATABASE: appdb
    volumes:
      - db-data:/var/lib/mysql

  backend:
    image: your-backend-image
    environment:
      DB_HOST: db
      DB_PORT: "3306"
      DB_NAME: appdb
    depends_on:
      - db

volumes:
  db-data:
```

## 2. Start Services

```bash
docker compose up -d
```

Replace `your-backend-image` with your actual backend image.

## ✅ Key Points
- `DB_HOST: db` uses the database service name.
- MySQL listens on port `3306` inside the Compose network.
- The database volume preserves data.
- Configure database credentials and connection settings according to your application.
- The backend must implement support for these environment variables.