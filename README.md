# Security Notes

Technical documentation and methodology notes from hands-on cybersecurity practice.

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
| [pwn.college](https://pwn.college) | Linux, binary basics |
| [TryHackMe](https://tryhackme.com) | Web security, PrivEsc |
| [Hack The Box](https://hackthebox.com) | Real-world scenarios |

---

## 🛠️ Tools Reference

| Category | Tools |
|----------|-------|
| Enumeration | LinPEAS, LinEnum |
| Binary | GTFOBins, strings, xxd |
| Network | nmap, netstat, ss |
| Web | Burp Suite, DevTools |

---

## 📈 Current Focus

- Linux privilege escalation vectors
- Automated enumeration techniques
- Web application security
- Shell scripting for security

---

*Documentation only. No flags or solutions.*
