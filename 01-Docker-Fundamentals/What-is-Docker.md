# What is Docker?

Docker is an **open-source platform** used to build, package, and run applications in **containers**.

A container includes the application and everything it needs to run, such as:
- Application code
- Libraries
- Dependencies
- Configuration

This makes applications run consistently across different environments.

## Why Docker?

Without Docker:
```text
Developer Machine → Testing Server → Production
       ❌              ❌                ❌
   Different      Different         Different
   Environment   Environment       Environment
```

With Docker:
```text
Application + Dependencies
          ↓
       Docker Image
          ↓
       Container
          ↓
Runs consistently everywhere
```

## Key Docker Concepts

| Concept | Description |
|---|---|
| **Image** | Read-only template used to create containers |
| **Container** | Running instance of an image |
| **Dockerfile** | File containing instructions to build an image |
| **Docker Hub** | Registry for sharing Docker images |
| **Docker Engine** | Technology that builds and runs containers |


## Docker Benefits

- Lightweight
- Fast startup
- Portable
- Consistent environments
- Easy deployment
- Efficient resource usage
- Easy application isolation

## Docker vs Virtual Machine

```text
Virtual Machine
Hardware
   ↓
Host OS
   ↓
Hypervisor
   ↓
Guest OS
   ↓
Application

Docker
Hardware
   ↓
Host OS
   ↓
Docker Engine
   ↓
Containers
   ↓
Applications
```

**In simple words:**  
> Docker packages an application with its dependencies into a container so it can run reliably in different environments.
