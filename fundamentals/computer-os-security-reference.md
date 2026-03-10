# Computer Fundamentals & OS Security Reference

Quick reference for computing fundamentals, virtualization, and OS security concepts.

---

## Hardware Components

| Component | Function |
|-----------|----------|
| CPU | Executes instructions |
| RAM | Temporary volatile memory |
| Storage | Permanent data storage |
| GPU | Graphics/compute processing |
| PSU | Power supply |
| Motherboard | Component interconnection |

---

## Boot Sequence

1. Power on → BIOS/UEFI → POST → Bootloader → OS → Login

---

## Virtualization

**VM:** Software-based computer inside host machine.

**Hypervisors:**
- Type 1: Bare-metal (directly on hardware)
- Type 2: On top of OS

**Use Cases:** Testing, isolation, malware analysis

---

## Kernel vs User Space

| Space | Access |
|-------|--------|
| Kernel | Full hardware access |
| User | Restricted (applications) |

---

## OS Security Components

- User accounts & authentication
- File permissions
- Firewalls
- Security updates/patches

---

## CLI Quick Reference

### Linux
```bash
pwd          # Current directory
ls           # List files
cd           # Change directory
cat          # View file
find         # Search files
```

### Windows
```cmd
dir          # List files
cd           # Change directory
type         # View file
systeminfo   # System info
ipconfig     # Network config
```

---

## Cloud Basics

**Providers:** AWS, Azure, Google Cloud

**Resources:** VMs, storage, databases, networks

**Connection:** SSH for remote access

---

## Client-Server Model

```
Client (request) → Server (response)
```

**HTTP:** GET/POST requests, status codes (200 OK, 404, etc.)
