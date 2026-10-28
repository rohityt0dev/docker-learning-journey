# Docker Network Troubleshooting

## 🎯 Objective
Learn how to identify and fix common Docker networking problems.

## 1. List Networks

```bash
docker network ls
```

## 2. Inspect a Network

```bash
docker network inspect app-network
```

## 3. Check Container Status

```bash
docker ps -a
```

## 4. Check Container Logs

```bash
docker logs my-container
```

## 5. Test DNS Resolution

```bash
docker exec app1 getent hosts app2
```

Ensure both containers are connected to the same user-defined network.

## 6. Test Container Communication

```bash
docker run --rm --network app-network curlimages/curl:latest http://app2
```

## 7. Check Port Mapping

```bash
docker port my-container
```

Run the container with port mapping if host access is required:

```bash
docker run -d --name web -p 8080:80 nginx
```

## 8. Common Problems

- **DNS failure:** Check network membership and container names.
- **Connection refused:** Check whether the application is running and listening on the correct port.
- **Timeout:** Check firewall rules, network configuration, and service availability.
- **Port inaccessible:** Verify port mapping and host firewall or cloud security rules.
- **Containers cannot communicate:** Connect them to the same suitable Docker network.

## 9. Cleanup

```bash
docker rm -f my-container
```

## ✅ Best Practices

- Use custom bridge networks.
- Use container names instead of hardcoded IP addresses.
- Inspect networks before changing configurations.
- Check application logs and listening ports.
- Avoid publishing ports unnecessarily.

## Summary

Docker network troubleshooting involves checking container status, network connections, DNS resolution, port mappings, and application availability.