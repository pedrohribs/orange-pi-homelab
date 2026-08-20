# Changelog

## Unreleased

### Added

- Initial repository structure.

> [Sprint 0.5 - Docker Fundamentals]

- Initial Docker documentation.
- Docker Desktop validation.
- Container lifecycle documentation.
- Docker volumes and networking fundamentals.
- First Docker Compose examples.

> [Sprint 1 - Orange Pi Base Infrastructure]

- Orange Pi 4 Pro hardware validation.
- microSD and NVMe storage validation.
- DietPi 10.6 deployment based on Debian 13 (Trixie).
- Wi-Fi and reserved IPv4 configuration.
- OpenSSH deployment replacing Dropbear.
- ED25519 public-key authentication.
- Administrative `dietpi` user with sudo privileges.
- SSH hardening with direct root login and password authentication disabled.
- UFW firewall with default-deny inbound policy.
- NVMe-backed DietPi userdata configuration.
- Docker Engine and Docker Compose deployment on the Orange Pi.
- Non-root Docker access for the administrative user.
- ARM64 container execution validation.
- Complete reboot and service recovery validation.
- ADR-001 updated following the DietPi operating system decision.
- ADR-002 added to document the microSD and NVMe storage architecture.
- NVMe boot troubleshooting documented.