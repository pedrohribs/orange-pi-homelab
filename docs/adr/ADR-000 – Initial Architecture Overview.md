# ADR-000 - Initial System Architecture

## Status

Accepted

---

## Context

Before any implementation, an initial system architecture was required to define the project scope and establish clear responsibilities for the Orange Pi 4 Pro.

The primary objective of this project is to build a lightweight, self-hosted homelab focused on learning infrastructure, Docker, Linux and DevOps-related concepts while maintaining simplicity, reproducibility and comprehensive documentation.

The architecture should remain intentionally small and avoid unnecessary services that do not directly contribute to the project's goals.

---

## Options Considered

### Option A

Start implementing services without defining an overall architecture.

### Option B

Design the complete high-level architecture before implementation.

---

## Decision

The project will follow a predefined high-level architecture before any implementation begins.

The initial architecture consists of four primary services:

- Pi-hole (Network-wide DNS and ad blocking)
- NAS + Plex (Media storage and streaming)
- Emulator Server (ROM and save storage)
- Lightweight Lab Environment (Technology experiments)

The following diagram represents the architecture after the initial Orange Pi deployment:

```text
                         Internet
                             |
                             v
                       Home Router
                             |
            +----------------+----------------+
            |                                 |
            v                                 v
   Windows Workstation                Orange Pi 4 Pro
   - VS Code                          - DietPi / Debian 13
   - Git                              - OpenSSH
   - SSH                              - Docker Engine
                                             |
                                             v
                                    +------------------+
                                    | Docker Services  |
                                    +------------------+
                                    | Pi-hole          |
                                    | NAS + Plex       |
                                    | Emulator Storage |
                                    | Lab Containers   |
                                    +------------------+
                                             |
                              +--------------+--------------+
                              |                             |
                              v                             v
                       microSD Storage                 NVMe Storage
                       - Boot                          - Docker data
                       - Operating System              - ROMs and saves
                       - System packages               - Media files
                                                       - Service data
---