# Orange Pi 4 Pro - Inconsistent NVMe Boot

## Symptoms

The Orange Pi 4 Pro was configured to boot a Debian installation stored directly on the NVMe SSD.

The NVMe itself was functional and the operating system could run correctly after a successful boot.

However, subsequent cold boots and reboots were inconsistent.

The board did not always start the operating system from the NVMe without additional intervention.

---

## Root Cause

The issue was not caused by NVMe storage failure.

Storage benchmarks and filesystem access confirmed that the NVMe SSD was operating correctly.

The unreliable behavior was related to the boot path used to start the operating system from NVMe through the board's bootloader/SPI configuration.

For this project, the SPI/NVMe boot path proved less predictable than booting directly from a microSD card.

---

## Investigation

The following areas were tested during troubleshooting.

### NVMe Detection

The NVMe SSD was successfully detected by Linux.

```bash
lsblk
```

The device appeared as:

```text
/dev/nvme0n1
```

This confirmed that the PCIe/NVMe interface itself was operational.

### NVMe Storage Validation

Read and write testing confirmed that the SSD operated normally after the system was running.

No evidence indicated that the inconsistent boot behavior was caused by storage failure.

### Operating System Installation

The Orange Pi Debian image was successfully written to the NVMe SSD.

The system was able to boot from the NVMe under the tested configuration.

However, subsequent boot attempts were not consistently successful.

### microSD Comparison

Booting the operating system directly from the microSD card was tested as an alternative.

The microSD boot process proved predictable and repeatable.

The system could then access the NVMe normally after Linux started.

This isolated the problem to the boot strategy rather than the NVMe device itself.

---

## Resolution

The project architecture was changed to use:

```text
microSD
└── Boot + Operating System

NVMe
└── Persistent application storage
```

DietPi is installed on the microSD card.

The NVMe SSD is formatted as ext4 and mounted at:

```text
/mnt/dietpi_userdata
```

Docker and future application data are stored on the NVMe.

This avoids depending on SPI/NVMe boot while still using the SSD for the workloads that benefit most from it.

---

## Validation

After changing the storage architecture, a complete reboot test was performed.

The system successfully restored:

- microSD root filesystem
- NVMe userdata mount
- Wi-Fi connectivity
- Reserved IPv4 address
- OpenSSH
- UFW
- Docker Engine
- Docker NVMe data directory

No manual intervention was required.

---

## Recommendation

For this project, microSD boot is the recommended configuration.

NVMe boot may still be possible and can be explored independently, but it is not required to reproduce the homelab.

Users with a sufficiently large microSD card can reproduce the entire project without an NVMe SSD.

When an NVMe SSD is available, using it for persistent workload storage is recommended.

---

## Lessons Learned

- Successful NVMe detection does not guarantee reliable NVMe boot.
- Storage functionality and bootloader functionality should be tested independently.
- A simpler boot architecture can be preferable even when faster storage is available.
- NVMe provides significant value as workload storage without being the system boot device.
- Boot reliability is more important than eliminating the microSD card from the architecture.