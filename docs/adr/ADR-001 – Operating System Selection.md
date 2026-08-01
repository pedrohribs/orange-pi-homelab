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

---

## Options Considered

### Orange Pi Debian

Official Debian image provided by the Orange Pi project.

### Armbian

Community-maintained Debian image with a newer Linux kernel (6.6 LTS), available only as a Rolling Release for the Orange Pi 4 Pro.

### Orange Pi Ubuntu Server

Official Ubuntu Server image provided by Orange Pi.

---

## Decision

The project will use the official Orange Pi Debian image.

---

## Rationale

Although Armbian provides newer software, better documentation and a larger community, the only image currently available for the Orange Pi 4 Pro is a community-maintained Rolling Release.

Since this project prioritizes long-term stability and predictable behavior over access to the latest software versions, a Rolling Release distribution introduces unnecessary operational risk.

The official Orange Pi Debian image offers:

- Official hardware support
- Better hardware compatibility
- Conservative kernel updates
- Predictable long-term behavior
- Lower maintenance requirements

Ubuntu Server was also considered. However, the project does not require any Ubuntu-specific features or enterprise integrations that would justify choosing it over Debian. Since Debian provides a smaller and more conservative base system, it better matches the project's objectives.

---

## Consequences

### Positive

- Official support for the target hardware.
- Stable and predictable platform.
- Lower probability of regressions caused by frequent operating system updates.
- Better alignment with the project's immutable infrastructure philosophy.

### Negative

- Older Linux kernel (5.15 LTS).
- Smaller community compared to Armbian.
- Slower access to newer kernel features.

---

## Decision Scope

This decision applies exclusively to the Orange Pi 4 Pro used in this project.

It should not be interpreted as a general recommendation against Armbian or Ubuntu Server. Different hardware platforms or project requirements may justify different operating system choices.