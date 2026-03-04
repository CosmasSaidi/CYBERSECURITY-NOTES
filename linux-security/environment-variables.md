# Environment Variables

`#linux` `#env`

## Why It Matters

Environment variables store configuration that programs read at runtime. Attackers can manipulate these to change program behavior, hijack execution paths, or leak sensitive information. Understanding them is essential for both offense and defense.

## Key Concepts

### What Are Environment Variables?

They're key-value pairs passed to processes:

```bash
# View all environment variables
env

# View specific variable
echo $PATH
echo $HOME
echo $USER
```

### Setting Variables

```bash
# Set for current shell only
MYVAR="hello"
echo $MYVAR

# Export to child processes
export MYVAR="hello"

# Set for one command only
MYVAR="test" ./program

# Unset a variable
unset MYVAR
```

### Important Security Variables

| Variable | Purpose | Security Impact |
|----------|---------|-----------------|
| `PATH` | Where shell looks for commands | Can be hijacked to run malicious binaries |
| `LD_PRELOAD` | Libraries loaded before others | Can inject code into programs |
| `HOME` | User's home directory | May affect where configs are read |
| `IFS` | Input Field Separator | Can change how shell parses input |

### Viewing Environment

```bash
# All variables
env
printenv

# Specific variable
printenv PATH
echo $PATH

# See what a program receives
env | grep -i path
```

## Common Mistakes

1. **Storing secrets in env vars** — They can be leaked via `/proc` or logs
2. **Trusting inherited environment** — Child processes inherit parent's env
3. **Not quoting variables** — `$VAR` can break if it contains spaces
4. **Modifying PATH unsafely** — Adding `.` to PATH is dangerous

## Safe Mini-Lab

```bash
# Create a safe test directory
mkdir /tmp/env-lab && cd /tmp/env-lab

# See your current environment
echo "PATH is: $PATH"
echo "HOME is: $HOME"

# Create a local variable (not exported)
LOCAL_VAR="local only"
echo $LOCAL_VAR

# Export a variable
export EXPORTED_VAR="I travel to child processes"

# Prove export works - run a subshell
bash -c 'echo "Local: $LOCAL_VAR"'      # Empty!
bash -c 'echo "Exported: $EXPORTED_VAR"' # Works!

# Clean up
cd && rm -rf /tmp/env-lab
unset LOCAL_VAR EXPORTED_VAR
```

## Defensive Takeaway

- **Sanitize environment** before running sensitive programs
- **Don't store secrets** in environment variables if avoidable
- **Use full paths** in scripts instead of relying on PATH
- **Quote your variables**: `"$VAR"` not `$VAR`
- **Check inherited environment** when debugging unexpected behavior

## Quick Checklist

- [ ] Used `export` when child processes need the variable
- [ ] Quoted variables properly: `"$VAR"`
- [ ] Avoided storing sensitive data in env vars
- [ ] Verified PATH doesn't contain `.` or writable directories
- [ ] Used `unset` to remove sensitive variables when done

## Further Practice

- Explore how `LD_PRELOAD` can affect program behavior
- Learn about `/proc/[pid]/environ` and why it's a security concern
- Practice with `env -i` to run commands with minimal environment
