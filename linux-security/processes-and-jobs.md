# Processes and Jobs

`#linux` `#processes`

## Why It Matters

Understanding processes helps you monitor what's running, detect suspicious activity, and control program execution. Attackers hide in processes; defenders must know how to find them.

## Key Concepts

### Viewing Processes

```bash
# Your processes
ps

# All processes, detailed
ps aux

# Process tree (shows parent-child)
ps auxf
pstree

# Real-time monitoring
top
htop  # (if installed, more user-friendly)
```

### Key Process Information

| Column | Meaning |
|--------|---------|
| PID | Process ID (unique identifier) |
| PPID | Parent Process ID |
| USER | Owner of the process |
| %CPU | CPU usage |
| %MEM | Memory usage |
| STAT | Process state |
| COMMAND | What's running |

### Process States

| State | Meaning |
|-------|---------|
| R | Running |
| S | Sleeping (waiting for event) |
| D | Uninterruptible sleep (usually I/O) |
| Z | Zombie (finished but parent hasn't cleaned up) |
| T | Stopped |

### Job Control

```bash
# Run in background
./long-task &

# List background jobs
jobs

# Bring job to foreground
fg %1

# Send running task to background
# First: Ctrl+Z (stops it)
# Then:
bg %1

# Kill a job
kill %1
```

### Signals

```bash
# Graceful termination
kill PID
kill -15 PID
kill -SIGTERM PID

# Force kill (last resort)
kill -9 PID
kill -SIGKILL PID

# Stop (pause)
kill -STOP PID

# Continue
kill -CONT PID
```

## Common Mistakes

1. **Using kill -9 first** — Always try graceful kill (-15) first
2. **Forgetting background jobs** — They continue running; use `jobs` to check
3. **Not checking process owner** — Suspicious if system process owned by regular user
4. **Ignoring zombie processes** — Usually indicates buggy parent process

## Safe Mini-Lab

```bash
# Start a background process
sleep 300 &
echo "Started sleep with PID: $!"

# View your jobs
jobs

# View the process
ps aux | grep sleep

# Bring to foreground
fg %1

# Stop it (Ctrl+Z)
# Now it's stopped

# Check jobs again
jobs
# Shows [1]+  Stopped  sleep 300

# Resume in background
bg %1

# Kill it gracefully
kill %1

# Verify it's gone
jobs
```

## Defensive Takeaway

- **Monitor regularly**: Know what processes are normal for your system
- **Check process owners**: Web server running as root? Investigate.
- **Watch for hidden processes**: Names with spaces or starting with `.`
- **Use `ps auxf`**: Tree view shows parent-child relationships
- **Log suspicious PIDs**: For later investigation

## Quick Checklist

- [ ] Can view all processes with `ps aux`
- [ ] Understand PID and PPID relationship
- [ ] Can use job control (bg, fg, jobs)
- [ ] Know difference between kill -15 and kill -9
- [ ] Can identify process state from STAT column

## Further Practice

- Learn about `/proc` filesystem and process information
- Explore `lsof` to see what files processes have open
- Practice with `strace` to trace system calls
- Study how to identify suspicious processes
