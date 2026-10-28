# Docker Container Communication

## 🎯 Objective
Learn how Docker containers communicate using Docker networks and container names.

## 1. Create a Network

```bash
docker network create app-network
```

## 2. Run Two Containers

```bash
docker run -d --name app1 --network app-network nginx
docker run -d --name app2 --network app-network nginx
```

## 3. Test Communication

```bash
docker exec app1 getent hosts app2
```

This command checks whether `app1` can resolve the name `app2`.


## 4. Important Points

- Containers on the same custom network can communicate using container names.
- Use container names instead of hardcoding IP addresses.
- Container-to-container communication does not require published ports.
- Use `-p` when you need to expose a container port through the host.

## 5. Inspect Network

```bash
docker network ls
docker network inspect app-network
```

## 6. Cleanup

```bash
docker rm -f app1 app2
docker network rm app-network
```

## Summary

Docker networks allow containers to communicate securely and conveniently using container names or network aliases.