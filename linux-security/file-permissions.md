# File Permissions

## Why It Matters
Misconfigured permissions are a common vulnerability. Understanding them is critical for both exploitation and hardening.

## Permission Structure

```
-rwxr-xr--
 │││││││││
 │││││││└┴─ Others: r-- (read)
 │││││└┴─── Group:  r-x (read, execute)
 ││││└┴──── Owner:  rwx (read, write, execute)
 │└┴─────── File type
```

## Commands

```bash
# View permissions
ls -la /path

# Modify permissions
chmod 755 script.sh     # rwxr-xr-x
chmod 600 secret.txt    # rw------- (owner only)
chmod u+x file          # Add execute for owner

# Change ownership
chown user:group file
```

## Octal Reference

| Value | Permission |
|-------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

## Security Relevance

**Finding misconfigurations:**
```bash
# World-writable files
find / -perm -002 -type f 2>/dev/null

# SUID binaries (run as owner)
find / -perm -4000 -type f 2>/dev/null

# SGID binaries
find / -perm -2000 -type f 2>/dev/null
```

SUID/SGID binaries can be privilege escalation vectors if misconfigured.
