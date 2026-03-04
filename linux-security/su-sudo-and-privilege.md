# su, sudo, and Privilege

`#linux` `#privilege`

## Why It Matters

Privilege escalation — gaining higher permissions than intended — is a core concept in security. Understanding how `su` and `sudo` work helps you use them safely and recognize when they're being abused.

## Key Concepts

### su (Switch User)

```bash
# Switch to root (requires root password)
su
su -

# Switch to another user
su username
su - username

# The dash (-) matters:
# su username  → keeps current environment
# su - username → loads target user's full environment
```

### sudo (Superuser Do)

```bash
# Run single command as root
sudo command

# Run command as different user
sudo -u username command

# Open root shell
sudo -i
sudo su -

# Edit files safely
sudo -e /etc/hosts
# or
sudoedit /etc/hosts
```

### Key Differences

| Feature | su | sudo |
|---------|-----|------|
| Password needed | Target user's password | Your password |
| Logged | No | Yes (in /var/log/auth.log) |
| Granular control | No | Yes (sudoers file) |
| Time limit | No | Yes (password cached briefly) |

### The sudoers File

```bash
# View sudo permissions
sudo -l

# Never edit directly; use:
sudo visudo
```

sudoers syntax example:
```
username ALL=(ALL:ALL) ALL
# user can run any command as any user on any host

username ALL=(ALL) NOPASSWD: /usr/bin/apt
# user can run apt without password
```

### Dangerous sudo Configurations

```bash
# Check what you can run
sudo -l

# Dangerous: NOPASSWD on everything
# Dangerous: sudo rights to editors (vim, nano) - can escape to shell
# Dangerous: sudo rights to interpreters (python, bash)
```

## Common Mistakes

1. **Running everything as root** — Use sudo for specific commands only
2. **Using `su` when `sudo` is safer** — sudo logs actions
3. **Leaving root shells open** — Exit when done
4. **Ignoring sudo logs** — These track privilege use
5. **NOPASSWD for sensitive commands** — Makes compromise easier

## Safe Mini-Lab

```bash
# Check your sudo permissions
sudo -l

# See the difference between su and su -
# (Don't run these unless you have permissions)
# su - loads full root environment
# su  keeps some of your environment

# View sudo log (if you have access)
sudo tail /var/log/auth.log | grep sudo

# See who's in sudo group
getent group sudo

# Check your groups
groups
id
```

## Defensive Takeaway

- **Prefer sudo over su**: It logs actions and offers fine-grained control
- **Use `-` with su**: `su -` loads clean environment
- **Exit elevated shells**: Don't leave root shells sitting open
- **Review sudo permissions**: `sudo -l` shows what you can do
- **Monitor logs**: `/var/log/auth.log` tracks privilege escalation
- **Principle of least privilege**: Grant minimum necessary permissions

## Quick Checklist

- [ ] Understand difference between su and sudo
- [ ] Know to use `su -` for full environment switch
- [ ] Can check sudo permissions with `sudo -l`
- [ ] Exit elevated shells when done
- [ ] Understand logging differences

## Further Practice

- Study the sudoers file format
- Learn about sudo timeout and timestamp
- Explore privilege escalation techniques (for defense)
- Practice with `sudo -u` to run as different users
