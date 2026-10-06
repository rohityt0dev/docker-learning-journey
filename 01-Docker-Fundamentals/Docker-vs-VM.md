# Docker vs Virtual Machine

Docker Containers and Virtual Machines (VMs) are both used to run applications in isolated environments, but they work differently.

## Architecture

### Virtual Machine

```text
┌─────────────────────────┐
│      Application        │
├─────────────────────────┤
│      Guest OS           │
├─────────────────────────┤
│      Hypervisor         │
├─────────────────────────┤
│       Host OS           │
├─────────────────────────┤
│       Hardware          │
└─────────────────────────┘
```

Each VM includes its own complete operating system.

### Docker

```text
┌─────────────────────────┐
│      Containers         │
│  ┌─────┐ ┌─────┐ ┌─────┐│
│  │ App │ │ App │ │ App ││
│  └─────┘ └─────┘ └─────┘│
├─────────────────────────┤
│      Docker Engine      │
├─────────────────────────┤
│        Host OS          │
├─────────────────────────┤
│        Hardware         │
└─────────────────────────┘
```

Containers share the host OS kernel.

## Key Differences

| Feature | Docker Container | Virtual Machine |
|---|---|---|
| Architecture | Container-based | Hardware virtualization |
| OS | Shares host kernel | Own guest OS |
| Startup | Seconds | Minutes |
| Size | Lightweight | Larger |
| Resource Usage | Low | Higher |
| Isolation | Process-level | Strong OS-level |
| Portability | High | High |
| Performance | Near-native | More overhead |
| Best For | Microservices, APIs, CI/CD | Full OS environments |

## Example

### Docker

```bash
docker run -d nginx
```

Starts an Nginx container quickly without requiring a complete guest OS.

### VM

A VM requires:

```text
Hardware
   ↓
Hypervisor
   ↓
Guest OS
   ↓
Dependencies
   ↓
Application
```

## When to Use Docker?

Use Docker when you need:

- Fast application deployment
- Lightweight environments
- Microservices
- CI/CD pipelines
- Application portability
- Development and testing environments

## When to Use VMs?

Use VMs when you need:

- A complete operating system
- Stronger isolation
- Different operating systems on the same host
- Legacy applications requiring a full OS

---