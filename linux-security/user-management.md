# User and Group Management

## Why It Matters
User accounts and privileges are primary targets. Understanding user management helps identify misconfigurations and escalation paths.

## Commands

```bash
# User information
whoami                  # Current user
id                      # User ID, groups
groups                  # Group memberships
cat /etc/passwd         # All users
cat /etc/shadow         # Password hashes (root only)
cat /etc/group          # All groups

# Switch users
su - username           # Switch user (need password)
sudo -l                 # List sudo privileges
sudo command            # Run as root
sudo -u user command    # Run as specific user
```

## Important Files

| File | Contents |
|------|----------|
| `/etc/passwd` | User accounts (readable by all) |
| `/etc/shadow` | Password hashes (root only) |
| `/etc/group` | Group definitions |
| `/etc/sudoers` | Sudo permissions |

## /etc/passwd Format

```
username:x:UID:GID:comment:home:shell
root:x:0:0:root:/root:/bin/bash
```

## Security Relevance

**Enumeration:**
```bash
# Users with shell access
grep -v "nologin\|false" /etc/passwd

# Users in sudo group
getent group sudo

# Check sudo permissions
sudo -l
```

**Common issues:**
- Weak sudo configurations
- Users in privileged groups
- Accounts with no password
- Service accounts with shell access
