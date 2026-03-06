# Linux Fundamentals

## Why It Matters
Linux powers most servers, security tools, and target systems. Mastery of the command line is essential for any security role.

## Essential Commands

```bash
# Navigation
pwd                     # Current directory
ls -la                  # List with permissions
cd /path                # Change directory

# File operations
cat file.txt            # View file
head -n 20 file         # First 20 lines
tail -f /var/log/syslog # Follow log in real-time
grep "pattern" file     # Search in file
find / -name "*.conf"   # Find files

# System info
uname -a                # Kernel info
hostname                # System name
id                      # Current user/groups
whoami                  # Current username
```

## File System Structure

| Path | Purpose |
|------|---------|
| `/etc` | Configuration files |
| `/var/log` | System logs |
| `/home` | User directories |
| `/tmp` | Temporary files (often world-writable) |
| `/root` | Root user home |
| `/bin`, `/usr/bin` | Executables |

## Security Relevance
- Configuration files may contain credentials
- Log files reveal system activity
- Temp directories are common attack vectors
- Understanding file locations speeds up enumeration
