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
|-----------|-------|
| SBC | Orange Pi 4 Pro |
| RAM | 4 GB LPDDR5 |
| Storage | SanDisk Ultra 32 GB microSD |
| Aditional Storage | 256 GB NVMe SSD |
| Operating System | Orange PI Debian |

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
├── assets/           # Images and other static repository assets
├── diagrams/         # Architecture and network diagrams
├── docker/           # Container and Docker Compose configurations
├── docs/
│   ├── adr/          # Architecture Decision Records
│   ├── architecture/ # Drawing of System Overview
│   ├── beginner/     # Beginner-friendly guides
│   ├── learning/     # Learning notes and studied concepts
│   ├── technical/    # Detailed technical documentation
│   └── troubleshooting/ # Documented problems and solutions
├── scripts/          # Automation, maintenance and backup scripts
├── LICENSE
├── README.md
└── ROADMAP.md

---

## Design Principles

- Simplicity over complexity.
- Every decision must be documented.
- Every service runs inside a Docker container whenever possible.
- Infrastructure should be reproducible.
- Documentation is as important as implementation.
- Security and backup are considered from the beginning.

---
## Documentation

The documentation is divided into multiple sections.

| Folder | Description |
|---------|-------------|
| docs/beginner | Beginner-friendly guides |
| docs/technical | Technical documentation |
| docs/adr | Architecture Decision Records |
| docs/troubleshooting | Problems and solutions |
| docs/learning | Personal learning notes |

---

## License

This project is licensed under the MIT License.