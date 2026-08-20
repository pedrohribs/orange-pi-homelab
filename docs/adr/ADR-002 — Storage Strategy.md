# ADR-002 - Storage Architecture

## Status

Accepted

---

## Context

The Orange Pi 4 Pro deployment has two available storage devices:

- SanDisk Ultra 32 GB microSD
- 256 GB NVMe SSD

The operating system must remain simple to recover while application workloads require faster and higher-capacity persistent storage.

Docker images, container layers, application data, media files and future NAS data may also generate significantly more write activity than the operating system itself.

A storage strategy was therefore required before deploying persistent workloads.

---

## Options Considered

### Option A

Store the operating system and all application data on the microSD card.

### Option B

Boot and run the entire operating system from the NVMe SSD.

### Option C

Use the microSD card for the operating system and the NVMe SSD for application and persistent workload data.

---

## Decision

The project will use the microSD card as the primary boot and operating system device.

The NVMe SSD will be used for DietPi userdata, Docker storage and persistent application data.

The deployed layout is:

```text
microSD
└── /
    ├── Boot
    ├── DietPi / Debian
    ├── System packages
    └── System configuration

NVMe
└── /mnt/dietpi_userdata
    ├── docker-data
    ├── Application data
    ├── Media
    ├── ROMs and saves
    └── Future persistent service data