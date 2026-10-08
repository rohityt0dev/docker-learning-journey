# Container Lifecycle

A Docker container goes through different states from **creation to removal**.

## Container Lifecycle

```text
             docker run
                  ↓
              Created
                  ↓
              Running
             ↙       ↘
      docker stop   docker restart
           ↓              ↓
        Stopped ←─────────┘
           ↓
       docker rm
           ↓
        Removed
```

## 1. Create and Start

Use `docker run`:

```bash
docker run -d --name my-nginx nginx
```

This command:

1. Creates a container
2. Starts the container
3. Runs it in the background

Check:

```bash
docker ps
```

## 2. Created State

You can create a container without starting it:

```bash
docker create --name my-nginx nginx
```

Check all containers:

```bash
docker ps -a
```

Start it:

```bash
docker start my-nginx
```

## 3. Running State

A running container can be viewed with:

```bash
docker ps
```

Example:

```text
CONTAINER ID   IMAGE   STATUS
abc123         nginx   Up 2 minutes
```

## 4. Stop a Container

Stop a running container:

```bash
docker stop my-nginx
```

The container changes from:

```text
Running → Stopped
```

The container still exists and can be started again.

## 5. Start a Stopped Container

```bash
docker start my-nginx
```

The container changes from:

```text
Stopped → Running
```

## 6. Restart a Container

```bash
docker restart my-nginx
```

This performs:

```text
Running
   ↓
Stopped
   ↓
Running
```

## 7. Pause a Container

Pause processes inside the container:

```bash
docker pause my-nginx
```

Resume:

```bash
docker unpause my-nginx
```

```text
Running
   ↓
Paused
   ↓
Running
```

## 8. Kill a Container

Forcefully stop a running container:

```bash
docker kill my-nginx
```

Unlike `docker stop`, `docker kill` does not wait for the application to shut down gracefully.

## 9. Remove a Container

Remove a stopped container:

```bash
docker rm my-nginx
```

Force remove a running container:

```bash
docker rm -f my-nginx
```

After removal:

```text
Container → Removed
```

## Container States

| State | Description |
|---|---|
| **Created** | Container exists but has not started |
| **Running** | Container is executing |
| **Paused** | Container processes are temporarily paused |
| **Stopped / Exited** | Container has stopped but still exists |
| **Removed** | Container no longer exists |

Check the state:

```bash
docker ps -a
```

## Useful Commands

```bash
docker create --name my-nginx nginx
docker start my-nginx
docker stop my-nginx
docker restart my-nginx
docker pause my-nginx
docker unpause my-nginx
docker kill my-nginx
docker rm my-nginx
```

## Inspect Container State

```bash
docker inspect my-nginx
```

You can also check only the current state:

```bash
docker inspect -f '{{.State.Status}}' my-nginx
```

Example:

```text
running
```

## Complete Lifecycle

```text
             docker create
                  ↓
              Created
                  ↓
             docker start
                  ↓
              Running
             ↙    ↓    ↘
       stop    pause    kill
        ↓        ↓       ↓
     Stopped   Paused  Stopped
        ↓        ↓
      start    unpause
        ↓        ↓
      Running ←─┘
        ↓
     docker rm
        ↓
     Removed
```

### Key Point

> **A container can be created, started, stopped, restarted, paused, resumed, and finally removed.**