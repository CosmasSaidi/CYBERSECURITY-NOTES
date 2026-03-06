# Environment Variables

## Why It Matters
Environment variables control program behavior. Manipulating them can bypass security controls or exploit vulnerable configurations.

## Commands

```bash
# View environment
env                     # All variables
echo $PATH              # Specific variable
printenv HOME           # Alternative method

# Set variables
export VAR="value"      # Available to child processes
VAR="value"             # Current shell only
unset VAR               # Remove variable
```

## Important Variables

| Variable | Purpose | Security Impact |
|----------|---------|-----------------|
| `PATH` | Command search path | PATH hijacking |
| `LD_PRELOAD` | Libraries to preload | Code injection |
| `HOME` | User home directory | Config file locations |
| `SHELL` | Default shell | Execution context |

## PATH Manipulation

```bash
# View current PATH
echo $PATH

# Add directory to PATH
export PATH="/my/dir:$PATH"

# Dangerous: current directory in PATH
export PATH=".:$PATH"   # Don't do this
```

## Security Relevance

**Exploitation:**
- PATH hijacking: Place malicious binary in earlier PATH directory
- LD_PRELOAD: Inject shared library into process

**Defense:**
- Use full paths in scripts: `/usr/bin/cat` not `cat`
- Validate environment before running privileged code
- Check for writable directories in PATH
