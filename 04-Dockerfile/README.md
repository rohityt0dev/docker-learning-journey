# Dockerfile Instructions

Learn the essential Dockerfile instructions used to build and configure Docker images.

## Topics

- [FROM](FROM.md) — Define the base image.
- [RUN](RUN.md) — Execute commands during image building.
- [CMD](CMD.md) — Specify the default command.
- [ENTRYPOINT](ENTRYPOINT.md) — Define the main executable.
- [COPY](COPY.md) — Copy files into the image.
- [ADD](ADD.md) — Copy files and extract supported archives.
- [WORKDIR](WORKDIR.md) — Set the working directory.
- [ENV](ENV.md) — Set environment variables.
- [ARG](ARG.md) — Define build-time variables.
- [EXPOSE](EXPOSE.md) — Document container ports.
- [USER](USER.md) — Set the execution user.
- [VOLUME](VOLUME.md) — Declare mount points.
- [HEALTHCHECK](HEALTHCHECK.md) — Check container health.

## Learning Path

```text
Dockerfile Basics
       ↓
Base Image (FROM)
       ↓
Install Dependencies (RUN)
       ↓
Configure Files and Environment
       ↓
Set Runtime (CMD / ENTRYPOINT)
       ↓
Build Docker Image
       ↓
Run Container
```

**Goal:** Understand each instruction and use it to build efficient, secure Docker images.
