# Security Fundamentals, Crypto & Recon Reference

Quick reference for CIA triad, encryption models, packet analysis, reconnaissance, encoding, and programming concepts used in cybersecurity.

---

## CIA Triad

| Principle | Goal |
|-----------|------|
| Confidentiality | Prevent unauthorized disclosure |
| Integrity | Prevent tampering or unauthorized modification |
| Availability | Keep systems and services accessible |

---

## Cryptography

### Encryption Models

| Type | Keys | Notes | Examples |
|------|------|-------|----------|
| Symmetric | One shared key | Fast, efficient, harder key distribution | AES, DES |
| Asymmetric | Public/private pair | Easier key exchange, slower | RSA, ECC |

### Distinctions

- **Encryption:** Protects confidentiality
- **Encoding:** Converts data format for transport
- **Hashing:** Supports integrity checks and password verification workflows

---

## Packet Analysis

### Common Filters

```text
icmp
dns
http
```

### Typical Layers Seen

- Frame
- Ethernet
- IP
- TCP/UDP
- DNS / HTTP

---

## Reconnaissance

### Goals

- Identify live systems
- Discover open ports
- Recognize exposed services
- Reduce unknown attack surface

### Common Tools

- `nmap`
- `curl`
- `WhatWeb`
- Browser developer tools

---

## Web Enumeration

### Common Findings

- Admin panels
- Login routes
- Upload directories
- Backups
- Static content folders

### Common Tools

- `Gobuster`
- `curl`
- Browser inspection

---

## Password Attack Awareness

### Defensive Priorities

- Strong password policy
- MFA
- Rate limiting
- Account lockout controls
- Log monitoring and alerting

### Common Tool

- `Hydra` for credential attack simulation in authorized labs

---

## Data Representation & Encoding

### Binary Example

| Decimal | Binary | Character |
|---------|--------|-----------|
| 65 | 01000001 | A |

### Useful Commands

```bash
echo "Hello" | xxd
echo "hello" | base64
echo "aGVsbG8=" | base64 -d
hexdump -C file.bin
```

---

## Programming Fundamentals

### Python

- Networking automation
- Scripting and parsing
- Security tooling foundations

### JavaScript

- Browser execution context
- Client-side logic
- Front-end attack surface awareness

### SQL

- Database queries
- Data access logic
- Injection risk awareness

### Node.js

- Server-side JavaScript runtime
- Common web backend structure awareness

---

## Pentesting Workflow

1. Reconnaissance
2. Scanning
3. Enumeration
4. Fingerprinting
5. Validation
6. Reporting
