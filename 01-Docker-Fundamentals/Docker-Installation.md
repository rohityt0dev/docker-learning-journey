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

sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
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
# Docker Installation — Amazon Linux 2023

This guide explains how to install and configure Docker on an **Amazon Linux 2023 EC2 instance**.

---

## Step 1 — Connect to EC2

Connect to your Amazon Linux EC2 instance using SSH.

```bash
ssh -i your-key.pem ec2-user@<EC2-PUBLIC-IP>
```

---

## Step 2 — Check the Current User

```bash
whoami
```

Expected:

```text
ec2-user
```

---

## Step 3 — Update the System

Update the installed packages:

```bash
sudo yum update -y
```

---

## Step 4 — Install Docker

Install Docker:

```bash
sudo yum install docker -y
```

Verify the installation:

```bash
docker --version
```

Example:

```text
Docker version 25.x.x
```

---

## Step 5 — Start Docker

Start the Docker service:

```bash
sudo systemctl start docker
```

Check the status:

```bash
sudo systemctl status docker
```

Expected:

```text
Active: active (running)
```

Press `q` to exit the status screen.

---

## Step 6 — Enable Docker at Boot

Enable Docker to start automatically after reboot:

```bash
sudo systemctl enable docker
```

---

## Step 7 — Add `ec2-user` to Docker Group

This allows `ec2-user` to run Docker commands without `sudo`.

```bash
sudo usermod -a -G docker ec2-user
```

---

## Step 8 — Test Docker

Check Docker information:

```bash
docker info
```

Run the Docker test container:

```bash
docker run hello-world
```

Docker should download the `hello-world` image and display a success message.

---
