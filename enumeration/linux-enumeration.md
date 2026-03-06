# Linux Enumeration

## Why It Matters
After gaining access, enumeration reveals escalation paths and valuable data.

## System Information

```bash
uname -a                # Kernel version
cat /etc/os-release     # OS details
hostname                # System name
cat /proc/version       # Kernel info
```

## User Enumeration

```bash
whoami                  # Current user
id                      # UID, GID, groups
sudo -l                 # Sudo permissions
cat /etc/passwd         # All users
cat /etc/shadow         # Password hashes (if readable)
history                 # Command history
```

## Network

```bash
ip a                    # Interfaces
netstat -tuln           # Listening ports
ss -tuln                # Alternative
cat /etc/hosts          # Host mappings
arp -a                  # ARP cache
```

## Interesting Files

```bash
# Configuration files
find / -name "*.conf" 2>/dev/null
cat /etc/crontab

# SUID binaries
find / -perm -4000 2>/dev/null

# Writable directories
find / -writable -type d 2>/dev/null

# Recent files
find / -mtime -1 2>/dev/null
```

## Credentials

```bash
# SSH keys
ls -la ~/.ssh/
cat ~/.ssh/id_rsa

# Bash history
cat ~/.bash_history

# Config files with passwords
grep -r "password" /etc/ 2>/dev/null
```

## Security Relevance
- SUID binaries may allow privilege escalation
- Readable config files may contain credentials
- Cron jobs may run vulnerable scripts
- Kernel version indicates potential exploits
