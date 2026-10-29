# 🐍 Dockerized Python Flask Application

## 📌 Project Overview

This project demonstrates how to containerize a Python Flask web application using Docker.

The application displays a welcome message on the homepage and provides a health-check endpoint to monitor application availability.

The Docker image packages Python, Flask, and the application code so the application can run consistently across different environments.

## 🎯 Objectives

- Build a web application using Python and Flask.
- Create a Dockerfile to containerize the application.
- Install dependencies using `requirements.txt`.
- Build and run a Docker image.
- Configure Docker port mapping.
- Implement a Docker health check.
- Run the application as a non-root user.
- Learn essential Docker commands.
- Prepare the project for GitHub.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Programming language |
| Flask | Web framework |
| Docker | Application containerization |
| Dockerfile | Image build instructions |
| Linux | Container host environment |
| Git | Version control |
| GitHub | Source code hosting |

## 📂 Project Structure

```text
flask-docker-app/
├── README.md
├── app.py
├── requirements.txt
├── Dockerfile
├── .dockerignore
└── .gitignore
```

## 🏗️ Application Architecture

```text
             User / Browser
                    |
                    | HTTP Request
                    |
                    v
           Host Port 8080
                    |
                    v
           Docker Container
                    |
                    v
             Flask App
              Port 5000
                    |
          +---------+---------+
          |                   |
          v                   v
      Homepage            Health Check
          |                   |
          v                   v
    Welcome Message      Status: Healthy
```

## ⚙️ Prerequisites

Install the following before starting:

- Docker Engine
- Git
- A terminal or Linux server
- A web browser or `curl`

Verify Docker installation:

```bash
docker --version
```

Check whether Docker is running:

```bash
docker info
```

## 🚀 Step 1: Clone the Repository

If the project is already on GitHub, clone it:

```bash
git clone https://github.com/YOUR_USERNAME/flask-docker-app.git
```

Navigate to the project directory:

```bash
cd flask-docker-app
```

Replace `YOUR_USERNAME` with your GitHub username.

## 🐳 Step 2: Build the Docker Image

Build the image:

```bash
docker build -t flask-docker-app:v1 .
```

Verify the image:

```bash
docker images
```

Expected image name:

```text
flask-docker-app
```

The tag is `v1`.

## ▶️ Step 3: Run the Container

Start the application:

```bash
docker run -d \
  --name flask-app \
  --publish 8080:5000 \
  flask-docker-app:v1
```

### Command explanation

- `-d`: Runs the container in the background.
- `--name flask-app`: Assigns a name to the container.
- `--publish 8080:5000`: Maps host port 8080 to container port 5000.
- `flask-docker-app:v1`: Specifies the image to run.

## 🔍 Step 4: Verify the Container

Check running containers:

```bash
docker ps
```

Check container health:

```bash
docker inspect --format='{{.State.Health.Status}}' flask-app
```

The health status should eventually become:

```text
healthy
```

The first health check may take several seconds because the Dockerfile defines a startup grace period.

## 🌐 Step 5: Access the Application

Open the following address on the Docker host:

```text
http://localhost:8080
```

Expected output:

```text
Hello from Dockerized Python App!
```

You can also test the application using `curl`:

```bash
curl http://localhost:8080
```

Expected output:

```text
Hello from Dockerized Python App!
```

## ❤️ Step 6: Test the Health Endpoint

Run:

```bash
curl http://localhost:8080/health
```

Expected response:

```json
{
  "status": "healthy"
}
```

This endpoint is used by the Docker health check.

## 📋 Step 7: View Container Logs

Display application logs:

```bash
docker logs flask-app
```

Follow the logs in real time:

```bash
docker logs -f flask-app
```

Press `Ctrl+C` to stop following the logs. This does not stop the container.

## 🛠️ Step 8: Container Management

Stop the container:

```bash
docker stop flask-app
```

Start it again:

```bash
docker start flask-app
```

Restart the container:

```bash
docker restart flask-app
```

Remove the container:

```bash
docker rm -f flask-app
```

List all containers:

```bash
docker ps -a
```

## 🧹 Step 9: Remove the Docker Image

After removing the container, remove the image if it is no longer needed:

```bash
docker rmi flask-docker-app:v1
```

## 📤 Step 10: Push the Project to GitHub

Initialize Git:

```bash
git init
```

Stage the files:

```bash
git add .
```

Commit the project:

```bash
git commit -m "Add Dockerized Flask application"
```

Create an empty repository on GitHub named `flask-docker-app`.

Connect the local repository to GitHub:

```bash
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/flask-docker-app.git
git push -u origin main
```

Replace `YOUR_USERNAME` with your GitHub username.

If a Git remote already exists, check it before adding another:

```bash
git remote -v
```

## 🧠 What I Learned

- Creating a Python Flask application.
- Writing a Dockerfile.
- Building Docker images.
- Running containers in detached mode.
- Publishing container ports.
- Monitoring application health.
- Inspecting container logs.
- Managing container lifecycle.
- Using `.dockerignore`.
- Running an application as a non-root user.
- Publishing source code to GitHub.

## 🔮 Future Improvements

- Add automated unit tests using `pytest`.
- Add a multi-stage Docker build if the application grows.
- Use Docker Compose for multi-container applications.
- Add CI/CD automation with Jenkins.
- Scan Docker images for vulnerabilities using Trivy.
- Deploy the application to an AWS EC2 instance.
- Add a reverse proxy using Nginx.
- Configure HTTPS for a production deployment.

## 👨‍💻 Author

**Your Name**

DevOps Learner | Docker | Linux | Git | Python

---

⭐ If you find this project useful, consider starring the repository on GitHub.