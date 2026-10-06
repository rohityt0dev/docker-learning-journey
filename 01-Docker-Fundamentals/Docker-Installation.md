# Docker Installation

Docker can be installed on **Linux, Windows, and macOS**.

> For learning Docker, Linux is commonly used because Docker runs natively on the Linux kernel.

## Linux — Ubuntu

### 1. Update Packages

```bash
sudo apt update
sudo apt upgrade -y
```

### 2. Install Required Packages

```bash
sudo apt install -y ca-certificates curl
```

### 3. Add Docker GPG Key

```bash
sudo install -m 0755 -d /etc/apt/keyrings

sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg \
  -o /etc/apt/keyrings/docker.asc

sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### 4. Add Docker Repository

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) \
  signed-by=/etc/apt/keyrings/docker.asc] \
  https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### 5. Install Docker

```bash
sudo apt update

sudo apt install -y \
  docker-ce \
  docker-ce-cli \
  containerd.io \
  docker-buildx-plugin \
  docker-compose-plugin
```

## Verify Installation

Check Docker version:

```bash
docker --version
```

Check Docker service:

```bash
sudo systemctl status docker
```

Run a test container:

```bash
sudo docker run hello-world
```

If successful, Docker is installed correctly.

## Run Docker Without `sudo`

Add your user to the Docker group:

```bash
sudo usermod -aG docker $USER
```

Apply the new group:

```bash
newgrp docker
```

Test:

```bash
docker run hello-world
```

> **Security Note:** Membership in the `docker` group effectively grants root-level privileges on the host. Use it only when appropriate.

## Useful Docker Service Commands

Start Docker:

```bash
sudo systemctl start docker
```

Stop Docker:

```bash
sudo systemctl stop docker
```

Restart Docker:

```bash
sudo systemctl restart docker
```

Enable Docker at boot:

```bash
sudo systemctl enable docker
```

Check status:

```bash
sudo systemctl status docker
```

## Troubleshooting

Check Docker information:

```bash
docker info
```

Check Docker service:

```bash
sudo systemctl status docker
```

View Docker logs:

```bash
sudo journalctl -u docker
```

## Windows & macOS

For Windows and macOS, the recommended approach for beginners is **Docker Desktop**.

Docker Desktop provides:

- Docker Engine
- Docker CLI
- Docker Compose
- Docker Build
- Container management

### Key Point

> **Install Docker Engine on Linux, or use Docker Desktop on Windows/macOS. After installation, verify it with `docker --version` and `docker run hello-world`.**