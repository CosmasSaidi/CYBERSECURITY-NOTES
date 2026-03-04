# Pipes and Redirection

`#bash` `#pipes`

## Why It Matters

Pipes and redirection connect programs together and control where data flows. They're essential for log analysis, data processing, and security tasks. Understanding them helps you build powerful one-liners and process large amounts of data efficiently.

## Key Concepts

### Pipes (|)

Connect stdout of one command to stdin of next:

```bash
# Basic pipe
cat file.txt | grep "error"

# Chain multiple commands
cat /var/log/syslog | grep "error" | head -10

# Real example: find failed logins
cat /var/log/auth.log | grep "Failed" | wc -l
```

### Standard Streams

| Stream | Number | Purpose |
|--------|--------|---------|
| stdin | 0 | Input (keyboard by default) |
| stdout | 1 | Normal output |
| stderr | 2 | Error messages |

### Output Redirection

```bash
# Redirect stdout to file (overwrite)
echo "hello" > file.txt

# Redirect stdout to file (append)
echo "world" >> file.txt

# Redirect stderr to file
command 2> errors.txt

# Redirect both stdout and stderr
command > output.txt 2>&1
command &> output.txt  # Bash shorthand

# Discard output
command > /dev/null 2>&1
```

### Input Redirection

```bash
# Read from file
sort < unsorted.txt

# Here document (multi-line input)
cat << EOF
Line 1
Line 2
