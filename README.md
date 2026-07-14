# Security Notes

Technical documentation and methodology notes from hands-on cybersecurity practice.

---

## 🌐 Networking & Internet Infrastructure

Core networking and Internet architecture study built through Internet Society and Cisco Packet Tracer learning.

### Completed / Participated Courses

- Fundamentals of Designing and Deploying Computer Networks
- Internet Governance
- What the Internet Needs to Exist
- What the Internet Needs to Thrive
- Introduction to Online Trust and Safety
- Community Network Readiness Assessment Program
- Community Networking Concepts and Deployment Readiness
- Cisco Packet Tracer Enterprise Networking

### Focus Areas

- Computer network design and deployment
- Internet infrastructure and architecture
- Community networking and deployment readiness
- Internet governance, trust, and safety
- TCP/IP, routing, switching, VLANs, DHCP, DNS, and troubleshooting
- Enterprise LAN segmentation with VLANs, IEEE 802.1Q trunking, SVIs, and inter-VLAN routing
- Layer 2 and Layer 3 switching architecture
- Dynamic and static routing protocols
- Network Address Translation (NAT)
- Wireless networking and enterprise service deployment
- Enterprise network design principles

### Technical Skills and Knowledge

**Networking Fundamentals:**
- MAC addressing, ARP, Ethernet communication
- ICMP ping and network diagnostic techniques
- Network device configuration (routers, switches, end devices)
- IP addressing and address verification

**Switching Technologies:**
- Layer 2 switching configuration and behavior
- MAC address learning and switch forwarding tables
- Broadcast domain management
- Multi-switch network topologies with star architecture
- Switch security configuration and management

**VLANs and Network Segmentation:**
- VLAN creation and port assignment
- IEEE 802.1Q trunk link configuration
- Switch Virtual Interfaces (SVIs) implementation
- Inter-VLAN routing for cross-segment communication
- IP subnetting for VLAN-to-subnet mapping
- Departmental network isolation and organization

**Enterprise LAN Design:**
- Hierarchical network topology design
- Layer 2 and Layer 3 switch deployment
- Departmental network segmentation (Admin, Finance, Students, Guests, Server Network)
- Enterprise architecture principles
- Scalable infrastructure design

**Routing Technologies:**
- Directly connected routes and routing table analysis
- Static route configuration
- Default route configuration
- OSPF dynamic routing protocol
- Automatic route exchange between routers

**Network Address Translation (NAT):**
- NAT purpose and role in enterprise networks
- Private IP address translation
- External network communication

**Enterprise Services:**
- DHCP scope configuration and automatic address allocation
- DNS name resolution and client configuration
- HTTP server deployment and client-server communication

**Wireless Networking:**
- Wireless access point configuration and wireless routers
- SSID configuration, wireless authentication, and client connectivity
- Guest wireless design and wireless segmentation

**Network Troubleshooting and Validation:**
- ICMP testing and ping utilities
- ARP resolution verification
- End-to-end connectivity testing
- Frame forwarding validation
- Fault isolation methodology
- Basic troubleshooting for addressing, VLAN assignment, trunking, and service issues

### Related Study Notes

- Networking planning and address assignment
- Topology design and validation with Packet Tracer
- Connectivity planning for enterprise and community environments
- Network sustainability and operational best practices
- Network deployment readiness and trust-focused Internet design
- Multi-switch enterprise topology validation with ARP/ICMP testing and basic fault isolation

---

## 📚 Topics

### 🐧 Linux Security

Core Linux concepts essential for security roles.

| Note | Description |
|------|-------------|
| [Fundamentals](linux-security/fundamentals.md) | Essential commands, file system structure |
| [File Permissions](linux-security/permissions.md) | chmod, octal notation, permission bits |
| [Process Management](linux-security/process-management.md) | ps, top, job control, signals |
| [Environment Variables](linux-security/environment-variables.md) | PATH, LD_PRELOAD, security implications |
| [User Management](linux-security/user-management.md) | Users, groups, sudo, privilege escalation |

**Key Commands:**
```bash
ls -la          # List with permissions
chmod 755 file  # Change permissions
ps aux          # List processes
env             # View environment
id              # User context
```

---

### 🔍 Enumeration

Post-exploitation enumeration techniques.

| Note | Description |
|------|-------------|
| [Linux Enumeration](enumeration/linux-enumeration.md) | System info, users, network, credentials |

**Quick Reference:**
```bash
# System
uname -a
cat /etc/os-release

# Users
whoami && id
sudo -l
cat /etc/passwd

# Network
ip a
netstat -tuln

# Interesting Files
find / -perm -4000 2>/dev/null  # SUID
find / -writable -type d 2>/dev/null
```

---

### 🌐 Web Security

Detection and response notes for common web attack behavior.

| Note | Description |
|------|-------------|
| [Web Discovery Detection & Response](web-security/web-discovery-detection-response.md) | Directory brute-force detection, SIEM triage, containment, WAF and rate limiting |
| [Web Fundamentals Reference](web-security/web-fundamentals-reference.md) | DNS, ICMP, topologies, OSI model, HTTP, cookies, HTML/JS, and injection risk concepts |

**Quick Detection Cues:**
```bash
# High-volume 404s from a single source IP can indicate scanning
# Repeated /admin, /backup, /config path probes are suspicious
```

---

### 🖥️ Fundamentals

Core computing concepts for security professionals.

| Note | Description |
|------|-------------|
| [Computer & OS Security Reference](fundamentals/computer-os-security-reference.md) | Hardware, boot process, virtualization, cloud, kernel vs user space, OS security |
| [Security Fundamentals, Crypto & Recon Reference](fundamentals/security-fundamentals-crypto-recon-reference.md) | CIA triad, encryption models, packet analysis, recon, encoding, and programming security concepts |
| [Terminal Bandit Session Journal](fundamentals/terminal-bandit-session-journal.md) | Full-session structured learning summary: OS, Linux, networking, crypto, hashing, NTLM risk, detection and remediation |

---

### 📋 Methodology

Structured approaches to security testing.

| Note | Description |
|------|-------------|
| [Linux Privilege Escalation](methodology/linux-privesc.md) | PrivEsc checklist and common vectors |

**Checklist:**
1. User Context (`whoami`, `id`, `sudo -l`)
2. System Info (`uname -a`)
3. SUID Binaries (`find / -perm -4000`)
4. Cron Jobs (`cat /etc/crontab`)
5. PATH Hijacking (`echo $PATH`)
6. Credentials (`grep -r "password" /etc/`)

---

### 💻 Shell Scripting

Automation for security tasks.

| Note | Description |
|------|-------------|
| [Bash Basics](shell-scripting/) | Scripting fundamentals |

---

### 🔧 Binary Exploitation

Binary analysis and exploitation basics.

| Note | Description |
|------|-------------|
| [Binary Basics](binary-exploitation/) | Understanding binaries |

---

### 🔄 Reverse Engineering

Understanding program behavior.

| Note | Description |
|------|-------------|
| [RE Basics](reverse-engineering/) | Reverse engineering fundamentals |

---

## 🎯 Practice Platforms

| Platform | Focus |
|----------|-------|
| [Internet Society](https://www.internetsociety.org/) | Internet architecture, governance, trust and safety |
| [Cisco Networking Academy](https://www.netacad.com/) | Routing, switching, Packet Tracer, deployment basics |
| [pwn.college](https://pwn.college) | Linux, binary basics |
| [TryHackMe](https://tryhackme.com) | Web security, PrivEsc |
| [Hack The Box](https://hackthebox.com) | Real-world scenarios |

---

## 🛠️ Tools Reference

| Category | Tools |
|----------|-------|
| Networking | Cisco Packet Tracer, Layer 2/Layer 3 switching, IEEE 802.1Q trunking, SVIs, inter-VLAN routing, Wireshark, nslookup, ping |
| Enumeration | LinPEAS, LinEnum |
| Binary | GTFOBins, strings, xxd |
| Network | nmap, netstat, ss, Wireshark |
| Web | Burp Suite, DevTools, WhatWeb, Gobuster |
| Auth Testing | Hydra |

---

## 📈 Current Focus

- Network architecture, routing, switching, and deployment readiness
- Linux privilege escalation vectors
- Automated enumeration techniques
- Web application security
- Shell scripting for security
- Cryptography fundamentals
- Network and web reconnaissance
- Linux systems administration, virtualization, enterprise infrastructure, Active Directory, cloud technologies, SOC operations, and cybersecurity engineering

---

*Documentation only. No flags or solutions.*
