# Command Substitution

`#bash` `#substitution`

## Why It Matters

Command substitution lets you capture command output and use it as data. It's powerful for automation but can be dangerous if you substitute untrusted input — leading to command injection vulnerabilities.

## Key Concepts

### Basic Syntax

```bash
# Modern syntax (preferred)
result=$(command)

# Legacy syntax (avoid in new code)
result=`command`
```

### How It Works

The shell:
1. Runs the command inside `$()`
2. Captures its stdout
3. Replaces `$()` with that output

```bash
# Store output in variable
current_date=$(date)
echo "Today is: $current_date"

# Use directly in commands
echo "You are: $(whoami)"
echo "Current dir: $(pwd)"

# Count files
file_count=$(ls | wc -l)
echo "Files in directory: $file_count"
```

### Nesting Substitutions

```bash
# Modern syntax nests cleanly
echo "First file: $(head -1 $(ls | head -1))"

# Backticks are messy to nest (avoid)
echo "First file: `head -1 \`ls | head -1\``"
```

### Common Patterns

```bash
# Get filename without path
filename=$(basename /path/to/file.txt)

# Get directory from path
dirname=$(dirname /path/to/file.txt)

# Process each line
while read line; do
    echo "Processing: $line"
done < <(cat file.txt)
```

## Common Mistakes

1. **Not quoting the result** — Breaks on spaces/special chars
   ```bash
   # Bad
   files=$(ls)
   # Good
   files="$(ls)"
   ```

2. **Using backticks for new code** — Harder to read and nest

3. **Forgetting stderr** — Only stdout is captured
   ```bash
   # Capture both stdout and stderr
   output=$(command 2>&1)
   ```

4. **Substituting untrusted input** — Command injection risk
   ```bash
   # DANGEROUS if $user_input is untrusted
   result=$(echo $user_input)
   ```

## Safe Mini-Lab

```bash
# Basic substitution
echo "Current user: $(whoami)"
echo "Home directory: $(echo $HOME)"

# Store in variable
my_shell=$(echo $SHELL)
echo "Your shell is: $my_shell"

# Use in conditions
if [ "$(whoami)" = "root" ]; then
    echo "Running as root!"
else
    echo "Running as regular user"
fi

# Count example
line_count=$(cat /etc/passwd | wc -l)
echo "Users in passwd: $line_count"

# Nested example
first_user=$(head -1 /etc/passwd | cut -d: -f1)
echo "First user: $first_user"
```

## Defensive Takeaway

- **Always quote**: `"$(command)"` handles spaces safely
- **Use `$()` not backticks**: Cleaner and nestable
- **Never substitute untrusted input**: Risk of command injection
- **Check exit status**: `$?` after substitution
- **Capture stderr if needed**: `$(cmd 2>&1)`

## Quick Checklist

- [ ] Using `$()` syntax (not backticks)
- [ ] Quoting substitutions: `"$(cmd)"`
- [ ] Not substituting untrusted user input
- [ ] Handling potential errors
- [ ] Capturing stderr when needed

## Further Practice

- Learn about process substitution: `<(command)`
- Explore `xargs` for processing command output
- Practice combining with pipes
- Study command injection vulnerabilities to defend against them
