# Docker Desktop - Virtualization Support Not Detected

## Symptoms

Docker Desktop failed to start and displayed the following message:

```text
Virtualization support not detected.
Docker Desktop failed to start because virtualization support wasn't detected.
```

Running:

```powershell
docker version
```

returned:

```text
Client:
...

failed to connect to the docker API at npipe:////./pipe/docker_engine
```

---

## Root Cause

Hardware virtualization (AMD SVM / Intel VT-x) was disabled in the BIOS.

Additionally, Windows Subsystem for Linux (WSL2) was not installed.

Docker Desktop relies on WSL2 to run Linux containers on Windows.

---

## Investigation

The following checks were performed:

> Check Docker Engine

```powershell
docker version
```

Only the **Client** section was displayed.

The **Server** section was missing, indicating that Docker Engine was not running.

---

>Check Docker Desktop

Docker Desktop displayed:

```text
Virtualization support not detected
```

---

>Check CPU Virtualization

Task Manager

```
Performance
→ CPU
→ Virtualization
```

Result:

```
Disabled
```

---

>Check WSL

```powershell
wsl --status
```

Result:

```
WSL was not installed.
```

---

## Resolution

1. Enable **SVM Mode (AMD)** in BIOS.
2. Install WSL2:

```powershell
wsl --install
```

3. Restart Windows.
4. Launch Docker Desktop.
5. Validate:

```powershell
docker version
```

Expected result:

```text
Client:
...

Server:
Docker Desktop
...
```

---

## Validation

Docker commands executed successfully:

```powershell
docker pull nginx
docker images
```

---

## Lessons Learned

Docker Desktop requires:

- Hardware virtualization enabled.
- WSL2 installed.
- Docker Engine running.

The Docker CLI can be installed and functional while Docker Engine is unavailable.