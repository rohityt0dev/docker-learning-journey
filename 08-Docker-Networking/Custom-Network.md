# Docker Custom Networks

## 🎯 Objective
Learn how to create and manage custom Docker networks.

## 1. Create a Custom Network

```bash
docker network create my-network
```

## 2. List Networks

```bash
docker network ls
```

## 3. Run Containers on the Network

```bash
docker run -d --name app1 --network my-network nginx
docker run -d --name app2 --network my-network nginx
```

## 4. Test Communication

```bash
docker exec app1 getent hosts app2
```

Containers on the same custom bridge network can communicate using container names.

## 5. Connect an Existing Container

```bash
docker network connect my-network my-container
```

## 6. Inspect Network

```bash
docker network inspect my-network
```

## 7. Disconnect a Container

```bash
docker network disconnect my-network my-container
```

## 8. Cleanup

```bash
docker rm -f app1 app2
docker network rm my-network
```

## ✅ Key Points

- Custom bridge networks provide automatic DNS resolution between containers.
- Containers can communicate without publishing ports to the host.
- Use container names instead of hardcoded IP addresses.
- Custom networks help organize and isolate application services.