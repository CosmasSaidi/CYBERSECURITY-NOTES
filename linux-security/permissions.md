# File Permissions
`#linux` `#permissions`

## Why It Matters
Misconfigured permissions = unauthorized access to files.

## Key Concepts
```bash
ls -la file.txt    # View permissions
# -rwxr-xr-- = owner(rwx) group(r-x) others(r--)
```

| Octal | Permission |
|-------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

```bash
chmod 755 script.sh   # rwxr-xr-x
chmod 600 secret.txt  # rw------- (owner only)
chmod u+x file        # Add execute for owner
```

## Common Mistakes
- Using `chmod 777` (world-writable)
- Forgetting `+x` on scripts

## Defensive Takeaway
Use minimum permissions needed. Never 777 in production.
