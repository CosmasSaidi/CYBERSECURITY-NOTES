# Linux Privilege Escalation Methodology

## Checklist

### 1. User Context
```bash
whoami
id
sudo -l
```

### 2. System Info
```bash
uname -a
cat /etc/os-release
```

### 3. SUID Binaries
```bash
find / -perm -4000 2>/dev/null
```
Check [GTFOBins](https://gtfobins.github.io) for exploitation.

### 4. Writable Files
```bash
find / -writable -type f 2>/dev/null
```

### 5. Cron Jobs
```bash
cat /etc/crontab
ls -la /etc/cron.*
```

### 6. PATH Hijacking
```bash
echo $PATH
# Check if writable directories are in PATH
```

### 7. Credentials
```bash
cat ~/.bash_history
grep -r "password" /etc/ 2>/dev/null
```

## Common Vectors
- Misconfigured sudo
- SUID binaries
- Writable scripts in cron
- Kernel exploits
- Credentials in config files
