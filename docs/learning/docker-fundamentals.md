# Docker Fundamentals

## Objective

This document summarizes the fundamental Docker concepts learned before starting the Orange Pi Homelab project.

The goal is to understand how containers work instead of simply following tutorials.

---

# Why Docker?

Docker was selected because it provides:

- Service isolation
- Reproducible environments
- Simplified deployments
- Easy maintenance
- Consistent behavior across different systems

---

# Virtual Machines vs Containers

Virtual machines virtualize an entire operating system, including its own kernel.

Containers share the host operating system kernel while isolating applications and their dependencies.

This makes containers significantly lighter and faster to start.

---

# Docker Architecture

Docker consists of several components:

### Docker CLI

Command-line interface used to communicate with Docker Engine.

Example:

```bash
docker run
docker ps
docker stop
```

---

### Docker Engine

Responsible for creating and managing containers, images, volumes and networks.

---

>### Docker Desktop

Windows application that provides Docker Engine through WSL2.

This component is not used on the Orange Pi.

---

### Docker Hub

Public registry used to download container images.

---

### Images

An image is a read-only template used to create containers.

Images contain:

- Operating system userspace
- Application
- Dependencies
- Default configuration

Images are immutable.

---

### Containers

A container is a running instance of an image.

Containers are intended to be disposable.

Stopping or removing a container should not result in data loss when persistence is correctly configured.

---

### Container Lifecycle

Basic lifecycle:

```text
Image
    ↓
docker pull
    ↓
docker run
    ↓
Running
    ↓
docker stop
    ↓
Stopped
    ↓
docker rm
```

---

### Port Mapping

Docker maps ports using the following syntax:

```text
HOST_PORT:CONTAINER_PORT
```

Example:

```text
8080:80
```

Requests sent to port 8080 on the host are forwarded to port 80 inside the container.

---

### Docker Volumes

Volumes provide persistent storage managed by Docker.

Volumes should be used for:

- Databases
- Application configuration
- User data
- Media libraries
- Save files

Removing a container does not remove its associated volume.

---

### Bind Mounts

Bind mounts expose an existing directory from the host system directly inside the container.

Typical use cases:

- Source code
- HTML files
- Scripts
- Configuration files under active development

Changes made on the host are immediately visible inside the container.

---

### Docker Networks

Docker creates isolated virtual networks for containers.

Containers connected to the same network can communicate using container names instead of IP addresses.

Example:

```text
ping web
```

Docker automatically resolves the container name through its internal DNS.

---

# Key Takeaways

- Containers are disposable.
- Data should be stored outside containers.
- Docker Volumes are preferred for persistent application data.
- Bind Mounts are preferred for editable project files.
- Docker Networks eliminate the need for static IP addresses between containers.
- Docker Compose is a declarative representation of these concepts.