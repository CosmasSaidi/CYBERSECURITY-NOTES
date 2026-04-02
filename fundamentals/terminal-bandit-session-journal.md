# Cybersecurity Learning Journal — Terminal Bandit

**Learner:** Cosmas Saidi  
**Program:** BSc Computer Science, Kenyatta University  
**Alias:** Terminal Bandit  
**Environment:** Kali Linux lab, virtual machines, AttackBox workflows  
**Platforms:** TryHackMe, pwn.college, personal lab practice

---

## Scope of This Session

This journal captures practical learning in:
- operating systems and shell fundamentals
- Linux command-line operations and process control
- networking, traffic analysis, and reconnaissance
- cryptography and hashing fundamentals
- password security and authentication risks
- incident-minded analysis of NTLM credential exposure patterns
- defensive detection and remediation concepts

This document is intentionally **methodology-focused** and excludes direct platform answers, flags, or walkthrough solutions.

---

## 1) Operating Systems and Shell Fundamentals

### Architecture Model
`User → Shell → Kernel → Hardware`

### Shell Families
- Linux: Bash, Zsh, Sh, Fish
- Windows: CMD, PowerShell

### CMD vs Linux Shell (Practical Contrast)
- CMD: basic command execution, lighter automation model
- Linux shell: pipelines, scripting, and automation-friendly workflows

### Representative Commands
- Windows: `dir`, `copy`, `ipconfig`
- Linux: `ls`, `pwd`, `cd`, `grep`, `chmod`

---

## 2) Linux Command-Line Skills

### Core Areas Practiced
- Navigation: `ls`, `cd`, `pwd`
- File operations: `cp`, `mv`, `rm`, `mkdir`, `touch`
- Ownership and permissions: `chmod`, `chown`
- Privilege context awareness: `su`, `sudo`
- Process/job handling: `ps`, `fg`, `bg`, `&`
- Environment variable handling: `export PATH=~/mybin:$PATH`

### Security Value
These skills support secure administration, post-exploitation analysis, and structured pentest workflows.

---

## 3) Networking Fundamentals

### Core Concepts
- client-server communication
- packet transmission
- IP addressing and service ports
- protocol-specific behavior

### Protocols Covered
- HTTP / HTTPS
- DNS
- FTP
- SMTP / POP3 / IMAP
- ICMP

---

## 4) Traffic Analysis and Reconnaissance

### Packet Analysis Tools
- Wireshark: visual protocol analysis
- tcpdump: terminal-based packet capture

Example:
```bash
tcpdump -i eth0
```

### Reconnaissance Skills
- host discovery
- port and service visibility
- service/version awareness
- attack surface mapping

Example:
```bash
nmap 10.10.10.10
nmap -sV 10.10.10.10
```

---

## 5) Cryptography and Hashing Foundations

### Cryptography Concepts
- plaintext / ciphertext lifecycle
- encryption vs decryption
- Caesar shift as historical model
- modulo arithmetic and XOR basics

### Encryption Models
- Symmetric: AES, DES
- Asymmetric: RSA, ECC

### Hashing Properties
- one-way
- deterministic
- fixed-length output

Algorithms reviewed:
- MD5
- SHA1
- SHA256
- SHA512

Practical uses:
- password verification
- integrity checks

---

## 6) Password Security and Cracking Awareness

### Storage Concepts
- Linux hashes: `/etc/shadow`
- Windows hashes: SAM-related storage model

### Tools Practiced
- John the Ripper
- Hashcat

### Attack Models Studied
- dictionary
- brute force
- rule-based mutation
- archive/SSH-hash conversion workflows

> Defensive takeaway: weak password policy and missing MFA materially increase compromise risk.

---

## 7) NTLM and Credential Exposure Concepts

### NTLM Learning Focus
- challenge-response behavior
- NetNTLMv2 capture risk in adversarial network paths
- hash cracking and pass-the-hash awareness

### Credential Capture Lab Pattern
- responder-based network capture simulation
- hash format interpretation and response planning

Example command:
```bash
sudo responder -I eth0
```

---

## 8) Case Study: Outlook Moniker Link Risk (CVE-2024-21413)

### Conceptual Attack Path (High-Level)
1. phishing delivery with crafted link
2. user interaction trigger
3. forced authentication attempt over attacker-controlled path
4. NetNTLMv2 material exposure

### Defensive Priorities
- patch management
- NTLM reduction/disablement where feasible
- outbound SMB controls
- anti-phishing controls and user awareness

---

## 9) Detection and Remediation Mindset

### Indicators to Monitor
- anomalous NTLM flows
- suspicious SMB outbound traffic
- phishing-linked authentication anomalies
- unusual external service connections

### Tools/Systems
- Wireshark
- SIEM workflows (e.g., Splunk-style triage)
- endpoint telemetry

### Mitigations
- rapid patching
- hardening legacy auth
- egress filtering
- user training and incident drills

---

## 10) Skills Consolidated

- Linux CLI and shell fluency
- network and protocol fundamentals
- packet inspection and recon methodology
- cryptography/hash literacy
- authentication risk analysis
- password security assessment concepts
- incident-oriented defensive reasoning

---

## Professional Note

This repository documents **learning methodology and security concepts only**. It does not publish direct challenge answers, flags, or platform-specific solutions.
