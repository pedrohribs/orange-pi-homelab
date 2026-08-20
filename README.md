# Orange Pi Homelab

> A documented homelab project built on an Orange Pi 4 Pro, focused on Linux, Docker, networking and DevOps practices.

## Project Scope

This repository documents the design, implementation and maintenance of a self-hosted infrastructure running on an Orange Pi 4 Pro.

Development environment preparation (Git, GitHub CLI, VS Code and other workstation tools) is intentionally considered out of scope. Those tools are prerequisites used to build the project, not part of the project itself.

---

## Project Goals

This project aims to build a small but realistic self-hosted infrastructure running on an Orange Pi 4 Pro.

Besides creating useful services for a home network, the main objective is to document every design decision, implementation step and troubleshooting process while studying Linux, Docker, networking and DevOps concepts.

The repository is intended to serve as both a learning journal and a technical portfolio.

---

## Hardware

| Component | Model |
|---|---|
| SBC | Orange Pi 4 Pro |
| RAM | 4 GB LPDDR5 |
| System Storage | SanDisk Ultra 32 GB microSD |
| Additional Storage | 256 GB NVMe SSD |
| Operating System | DietPi / Debian 13 (Trixie) |

The microSD card is used for the operating system and system packages.

The NVMe SSD is mounted at `/mnt/dietpi_userdata` and is used for persistent application data, Docker storage and future service data.

The project can still be reproduced using only a sufficiently large microSD card. The NVMe SSD is part of the deployed architecture, but it is not a strict requirement for reproducing the homelab.

---

## Current Base Infrastructure

The Orange Pi currently operates as a primarily headless Linux server.

The validated baseline includes:

- DietPi 10.6 based on Debian 13 (Trixie)
- Linux 6.6 vendor kernel
- Wi-Fi as the primary network interface
- Reserved IPv4 address
- OpenSSH
- ED25519 public-key authentication
- Administrative `dietpi` user with sudo privileges
- Direct root SSH login disabled
- SSH password authentication disabled
- UFW firewall
- Docker Engine
- Docker Compose
- NVMe-backed DietPi userdata
- LXDE as an optional local recovery interface
- Firefox as the fallback graphical browser

Normal administration is performed remotely through SSH.

---

## Planned Services

- Pi-hole (Network-wide DNS ad blocker)
- NAS
- Plex Media Server
- ROM and Save Storage
- Docker Laboratory
- Monitoring
- Backup

---

## Repository Structure

```text
.
├── assets/              # Images and other static repository assets
├── diagrams/            # Architecture and network diagrams
├── docker/              # Container and Docker Compose configurations
├── docs/
│   ├── adr/             # Architecture Decision Records
│   ├── beginner/        # Beginner-friendly guides
│   ├── learning/        # Learning notes and studied concepts
│   ├── technical/       # Detailed technical documentation
│   └── troubleshooting/ # Documented problems and solutions
├── scripts/             # Automation, maintenance and backup scripts
├── LICENSE
├── README.md
└── ROADMAP.md