# Process Management

## Why It Matters
Understanding running processes helps identify suspicious activity, find vulnerable services, and manage system resources during testing.

## Commands

```bash
# View processes
ps aux                  # All processes
ps auxf                 # Process tree
top                     # Real-time monitor
pstree                  # Visual tree

# Process details
ps aux | grep nginx     # Find specific process
lsof -p PID             # Files opened by process
lsof -i :80             # What's using port 80

# Job control
command &               # Run in background
jobs                    # List background jobs
fg %1                   # Bring to foreground
bg %1                   # Resume in background
Ctrl+Z                  # Suspend current process
```

## Key Process Info

| Column | Meaning |
|--------|---------|
| PID | Process ID |
| PPID | Parent process ID |
| USER | Process owner |
| %CPU | CPU usage |
| COMMAND | What's running |

## Signals

```bash
kill PID                # Graceful termination
kill -9 PID             # Force kill
kill -STOP PID          # Pause process
kill -CONT PID          # Resume process
```

## Security Relevance
- Identify services running as root
- Find processes with network connections
- Detect hidden or suspicious processes
- Background tasks for long-running scans
