# ADR-001 - Operating System Selection

## Status

Accepted

---

## Context

The Orange Pi 4 Pro requires an operating system that will serve as the foundation for all services deployed throughout this project.

The primary goals of this homelab are:

- Long-term stability
- Predictable behavior
- Low maintenance
- Hardware compatibility
- Reproducibility
- Educational value

The operating system should remain as stable as possible, allowing the project to focus on infrastructure and services rather than operating system maintenance.

The operating system selection was revisited during Phase 1 because DietPi added support for the Orange Pi 4 Pro after the original architectural decision had already been made.

This introduced a new viable option that was not available during the initial evaluation.

---

## Options Considered

### Orange Pi Debian

Official Debian image provided by the Orange Pi project.

This was the original operating system selected for the project.

It provided:

- Official hardware support
- Predictable hardware compatibility
- Conservative software versions
- Debian package ecosystem

The tested image used Debian 12 with the Orange Pi vendor Linux 5.15 kernel.

### Armbian

Community-maintained Debian-based distribution with a newer Linux kernel.

The available Orange Pi 4 Pro image uses a newer vendor kernel but remains community-supported and follows a rolling release model.

This conflicts with the project's preference for predictable and conservative system updates.

### Orange Pi Ubuntu Server

Official Ubuntu Server image provided by Orange Pi.

Ubuntu-specific features and integrations are not required by this project, and using Ubuntu would not provide a meaningful advantage over a Debian-based environment.

### DietPi

Lightweight Debian-based distribution designed primarily for SBCs and server workloads.

Orange Pi 4 Pro support became available after the original operating system decision.

The tested deployment provides:

- DietPi 10.6
- Debian 13 (Trixie)
- Linux 6.6 vendor kernel
- ARM64 support
- Lightweight headless baseline
- Integrated system configuration tools
- Integrated software installation
- Dedicated userdata structure

---

## Original Decision

The original decision selected the official Orange Pi Debian image.

At the time, it provided the best balance between hardware compatibility, stability and predictable maintenance.

Armbian was rejected because the available Orange Pi 4 Pro build followed a rolling release model.

Ubuntu Server was rejected because the project did not require Ubuntu-specific functionality.

DietPi was not part of the original viable alternatives because Orange Pi 4 Pro support was not yet available.

---

## Revised Decision

The project will use DietPi based on Debian 13 (Trixie).

The deployed system uses the Orange Pi vendor Linux 6.6 kernel.

The official Orange Pi Debian image remains a valid fallback option if DietPi-specific compatibility issues are discovered in the future.

---

## Rationale

The decision was revisited because DietPi support for the Orange Pi 4 Pro became available after the original ADR was written.

The new option was evaluated directly on the target hardware instead of changing the architecture based only on specifications.

Testing confirmed:

- Successful microSD boot
- Stable Wi-Fi connectivity
- Ethernet support
- NVMe detection and operation
- OpenSSH operation
- Docker Engine operation
- Docker Compose operation
- ARM64 container execution
- Stable system reboot
- Low baseline memory usage
- Stable operating temperatures

DietPi provides a newer Debian stable base and a newer vendor kernel while preserving the Debian ecosystem originally selected for the project.

It also provides integrated tooling specifically designed for lightweight SBC and server deployments.

The distribution remains minimal by default while still allowing optional components to be installed when required.

For this deployment, LXDE and Firefox were installed as a lightweight local recovery environment. They are not part of the normal administration workflow, which remains SSH-based.

---

## Consequences

### Positive

- Debian 13 stable base.
- Newer Linux 6.6 vendor kernel.
- Very low baseline resource usage.
- Good compatibility with the Orange Pi 4 Pro.
- Integrated SBC-focused configuration tools.
- Native DietPi userdata organization.
- Straightforward Docker and Docker Compose deployment.
- Debian administration concepts remain applicable.
- Optional graphical recovery environment without requiring graphical boot.

### Negative

- Adds DietPi-specific tooling on top of Debian.
- Some configuration differs from a vanilla Debian installation.
- Hardware support still depends partly on the Orange Pi vendor kernel.
- Documentation must distinguish DietPi-specific behavior from standard Debian behavior.

---

## Decision Scope

This decision applies exclusively to the Orange Pi 4 Pro used in this project.

It should not be interpreted as a general recommendation against Armbian, Ubuntu Server or the official Orange Pi Debian image.

Different hardware platforms or project requirements may justify different operating system choices.

---

## Revision History

| Version | Description |
|---|---|
| 1.0 | Official Orange Pi Debian selected as the operating system. |
| 1.1 | Decision revisited after DietPi added Orange Pi 4 Pro support. DietPi / Debian 13 selected after successful hardware validation. |