# Web and Database with Docker

## 🎯 Objective
Learn how a web service can communicate with a database using Docker Compose.

## 1. Create `compose.yaml`

```yaml
services:
  db:
    image: mysql:8
    environment:
      MYSQL_ROOT_PASSWORD: example-password
      MYSQL_DATABASE: appdb
    volumes:
      - db-data:/var/lib/mysql

  web:
    image: phpmyadmin:latest
    ports:
      - "8080:80"
    environment:
      PMA_HOST: db
    depends_on:
      - db

volumes:
  db-data:
```

## 2. Start Services

```bash
docker compose up -d
```

## 3. Access phpMyAdmin

Open `http://localhost:8080`.

Use the MySQL root account and the password configured in the Compose file.

## 4. Cleanup

```bash
docker compose down
```

## ✅ Key Points
- Services communicate using their Compose service names.
- The named volume persists database data.
- `depends_on` controls startup order but does not guarantee database readiness.
- The example password is for learning only; use secure credentials for real applications.