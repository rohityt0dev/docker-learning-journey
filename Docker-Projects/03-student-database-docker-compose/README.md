# Student Database Management Using Docker Compose

## 📌 Project Overview

This project demonstrates how to deploy MongoDB and Mongo Express using Docker Compose.

MongoDB stores student records, while Mongo Express provides a web-based interface for managing databases and collections.

## 🛠️ Technologies Used

- Docker
- Docker Compose
- MongoDB
- Mongo Express
- YAML
- Git and GitHub

## 🏗️ Architecture

```text
Browser
   |
   v
Mongo Express :8081
   |
   v
MongoDB :27017
   |
   v
Named Docker Volume
```

## 📂 Project Structure

```text
student-database-docker-compose/
├── compose.yaml
├── .env
├── .gitignore
└── README.md
```

## 🚀 Setup Instructions

### 1. Clone the repository

```bash
git clone <your-repository-url>
cd student-database-docker-compose
```

### 2. Configure environment variables

Create a `.env` file:

```dotenv
MONGO_USERNAME=root
MONGO_PASSWORD=ChangeThisPassword123
```

Use a strong password and keep `.env` out of version control.

### 3. Start the services

```bash
docker compose up -d
```

### 4. Check the containers

```bash
docker compose ps
```

### 5. Open Mongo Express

Visit:

```text
http://localhost:8081
```

### 6. Stop the services

```bash
docker compose down
```

## 🗄️ Database Details

- Database: `studentdb`
- Collection: `students`

Example student document:

```json
{
  "student_id": 101,
  "name": "Rahul",
  "age": 22,
  "course": "DevOps",
  "city": "Mumbai"
}
```

## 💾 Data Persistence

A named Docker volume stores MongoDB data.

```yaml
volumes:
  - mongodb_data:/data/db
```

The database data persists when containers are removed and recreated, provided the volume is retained.

## 📚 What I Learned

- Creating multi-container applications with Docker Compose
- Configuring MongoDB using environment variables
- Connecting containers through a Docker network
- Using Mongo Express to manage database records
- Creating and using named Docker volumes
- Performing basic MongoDB CRUD operations
- Inspecting containers and troubleshooting logs
- Managing project configuration with YAML

## 🔒 Security Notes

- Do not commit `.env` to GitHub.
- Do not use example credentials in production.
- Restrict published ports to trusted interfaces.
- Use appropriate authentication and network controls.

## 👨‍💻 Author

Add your name and GitHub profile here.