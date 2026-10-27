# Docker Bind Mounts

## Objective

Learn how to share files and directories between the host machine and a Docker container using bind mounts.

## 1. What Is a Bind Mount?

A **bind mount** connects a specific file or directory on the host machine to a path inside a container.

Changes made to mounted files can be reflected on both the host and container.

## 2. Create a Host Directory

```bash
mkdir -p /home/ec2-user/html
echo "Hello from Docker Bind Mount" > /home/ec2-user/html/index.html
```

## 3. Run a Container with a Bind Mount

```bash
docker run -d \
  --name my-nginx \
  -p 8080:80 \
  --mount type=bind,source=/home/ec2-user/html,target=/usr/share/nginx/html \
  nginx
```

-

  `source` — Directory on the host machine.
- `target` — Directory inside the container.
- `-p 8080:80` — Maps host port 8080 to container port 80.

Open `http://localhost:8080` to view the page. If using a remote EC2 instance, access its public address on port `8080` and ensure the security group allows that port.

## 4. Update the File

On the host machine, run:

```bash
echo "Updated Bind Mount Content" > /home/ec2-user/html/index.html
```

Refresh the browser to see the updated content.

## 5. Inspect the Bind Mount

```bash
docker inspect my-nginx
```

Look for the `Mounts` section to see the source and destination paths.

## 6. Remove the Container

```bash
docker rm -f my-nginx
```

Removing the container does **not** delete the files in the host directory.

## Bind Mount vs Volume

| Feature           | Bind Mount                   | Docker Volume               |
| ----------------- | ---------------------------- | --------------------------- |
| Storage location  | Specific host path           | Managed by Docker           |
| Host file access  | Direct                       | Usually through Docker      |
| Common use        | Development and file sharing | Persistent application data |
| Container removal | Host files remain            | Volume data remains         |

## Best Practices

- Use absolute paths for bind mounts.
- Ensure the host directory exists and has appropriate permissions.
- Avoid mounting sensitive host files into containers.
- Use read-only mounts when containers do not need to modify files.

Example read-only mount:

```bash
docker run -d \
  --name my-nginx \
  --mount type=bind,source=/home/ec2-user/html,target=/usr/share/nginx/html,readonly \
  nginx
```

## Summary

Bind mounts let containers access specific files and directories on the host. They are especially useful during development when you want host-side file changes to appear inside a container.
