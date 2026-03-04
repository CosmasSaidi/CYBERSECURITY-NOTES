# PATH and Execution

`#linux` `#path`

## Why It Matters

When you type a command like `ls`, the shell searches directories in your PATH variable to find the executable. Attackers can exploit this by placing malicious binaries in PATH directories or manipulating PATH to hijack command execution.

## Key Concepts

### How PATH Works

```bash
# View your PATH
echo $PATH
# /usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

# Shell searches left to right
# First match wins
```

### Command Resolution Order

When you type `cat`:
1. Shell checks if it's an alias
2. Shell checks if it's a function
3. Shell checks if it's a builtin
4. Shell searches PATH directories (left to right)
5. First executable found is run

```bash
# See exactly what will run
which cat
type cat
command -v cat
```

### Modifying PATH

```bash
# Add to beginning (searched first)
export PATH="/my/dir:$PATH"

# Add to end (searched last)
export PATH="$PATH:/my/dir"

# Temporarily for one command
PATH="/safe/path" ./program
```

### The Current Directory Problem

```bash
# DANGEROUS: Adding . (current directory) to PATH
export PATH=".:$PATH"

# Why? Attacker could place malicious 'ls' in any directory
# When you cd there and type 'ls', you run their code
```

## Common Mistakes

1. **Adding `.` to PATH** — Allows current-directory hijacking
2. **Adding writable directories to PATH** — Others can plant malicious binaries
3. **Not using full paths in scripts** — Scripts may run in unexpected PATH contexts
4. **Forgetting PATH order matters** — First match wins

## Safe Mini-Lab

```bash
# Create safe test environment
mkdir -p /tmp/path-lab/bin && cd /tmp/path-lab

# Create a fake "ls" command
cat > bin/myls << 'SCRIPT'
#!/bin/bash
echo "This is my custom ls"
SCRIPT
chmod +x bin/myls

# Current PATH doesn't include our directory
which ls           # /usr/bin/ls
myls               # Command not found

# Add our directory to PATH
export PATH="/tmp/path-lab/bin:$PATH"
which myls         # /tmp/path-lab/bin/myls
myls               # "This is my custom ls"

# See the danger: if this was named 'ls' it would override the real one

# Reset PATH (important!)
export PATH="/usr/local/bin:/usr/bin:/bin"

# Clean up
cd && rm -rf /tmp/path-lab
```

## Defensive Takeaway

- **Never add `.` to PATH** — Use `./script` explicitly
- **Use full paths in scripts**: `/usr/bin/cat` not `cat`
- **Verify PATH contents**: `echo $PATH | tr ':' '\n'`
- **Check for writable PATH directories**: These are attack vectors
- **Reset PATH** when running sensitive operations

## Quick Checklist

- [ ] PATH doesn't contain `.` (current directory)
- [ ] PATH doesn't contain world-writable directories
- [ ] Scripts use full paths for critical commands
- [ ] Verified which binary runs with `which` or `type`
- [ ] Understand left-to-right search order

## Further Practice

- Create a script that validates PATH for security issues
- Learn about `env -i` to run commands with clean environment
- Explore how setuid programs handle PATH differently
