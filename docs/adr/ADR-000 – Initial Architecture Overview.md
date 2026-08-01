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

The following diagram represents the initial architecture.
  
                Internet
                    │
                    │
             Home Router
                    │
         ┌──────────┴──────────┐
         │                     │
    Windows Workstation    Orange Pi
         │                     │
         │ SSH                 │
         │ Git                 │
         │ VS Code             │
         │                     │
         └────────────┬────────┘
                      │
                   Docker
      ┌───────────────┼──────────────┐
      │               │              │
   Pi-hole         NAS/Plex      Lab Containers
   *

---

## Rationale

This architecture was selected because it:

- Defines a clear project scope.
- Prioritizes educational value over feature count.
- Matches the available hardware resources.
- Supports incremental development through sprints.
- Avoids unnecessary complexity.
- Can be expanded in future revisions without redesigning the entire system.

---

## Consequences

### Positive

- Well-defined project scope.
- Easier documentation.
- Simpler maintenance.
- Lower hardware requirements.
- Clear roadmap for future sprints.

### Negative

- Some commonly used homelab services are intentionally excluded.
- Future architectural changes may require updates to this ADR.

---

## Revision History

| Version | Description |
|----------|-------------|
| 1.0 | Initial system architecture defined before implementation. |