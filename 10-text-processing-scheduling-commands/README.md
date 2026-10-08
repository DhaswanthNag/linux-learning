# Linux Command-Line Utilities Reference

A practical guide to common Linux commands for **searching, filtering, transforming, scheduling, and monitoring files and processes**.

> Examples assume a Linux/macOS shell such as Bash or Zsh. Run `man <command>` or `<command> --help` for the complete manual.

---

## Table of Contents

- [1. `grep`](#1-grep)

- [2. `egrep` / `grep -E`](#2-egrep--grep--e)

- [3. `sed`](#3-sed)

- [4. `awk`](#4-awk)

- [5. `cut`](#5-cut)

- [6. `sort`](#6-sort)

- [7. `uniq`](#7-uniq)

- [8. `wc`](#8-wc)

- [9. `tr`](#9-tr)

- [10. `tee`](#10-tee)

- [11. `xargs`](#11-xargs)

- [12. `crontab`](#12-crontab)

- [13. `crontab -l`](#13-crontab--l)

- [14. `at`](#14-at)

- [15. `watch`](#15-watch)

- [16. Useful Pipelines](#16-useful-pipelines)

- [17. Important Safety Notes](#17-important-safety-notes)

---

## 1. `grep`

`grep` searches for text or patterns inside files and prints matching lines.

### Syntax

```bash
grep [OPTIONS] PATTERN [FILE...]
```

### Basic examples

```bash
# Search for the word "error" in a file
grep "error" app.log

# Search in multiple files
grep "error" app.log server.log

# Search all files in the current directory
grep "error" *

# Search recursively in the current directory
grep -r "error" .
```

### Common options

| Option | Meaning |
| --- | --- |
| `-i` | Ignore uppercase/lowercase differences |
| `-v` | Print lines that do **not** match |
| `-n` | Show line numbers |
| `-r` or `-R` | Search recursively through directories |
| `-w` | Match complete words only |
| `-c` | Count matching lines |
| `-l` | Print only filenames containing a match |
| `-L` | Print only filenames without a match |
| `-h` | Hide filenames in output |
| `-o` | Print only the matching portion |
| `-A N` | Print `N` lines after each match |
| `-B N` | Print `N` lines before each match |
| `-C N` | Print `N` lines before and after each match |
| `-E` | Use extended regular expressions |
| `-F` | Search for a fixed string, not a regular expression |

### Examples with options

```bash
# Case-insensitive search
grep -i "failed" login.log

# Show matching lines with line numbers
grep -n "TODO" script.py

# Search recursively, showing filenames and line numbers
grep -rn "DATABASE_URL" .

# Count lines containing "404"
grep -c "404" access.log

# Show lines that do not contain "localhost"
grep -v "localhost" config.txt

# Show three lines of context around each match
grep -C 3 "Exception" application.log

# Search only selected files recursively
grep -r --include="*.java" "@RestController" src/
```

### Search command output

```bash
ps aux | grep "nginx"
```

To avoid matching the `grep` command itself:

```bash
ps aux | grep "[n]ginx"
```

---

## 2. `egrep` / `grep -E`

`egrep` is the older name for `grep -E`. Both use **extended regular expressions**. Prefer `grep -E` in new scripts because `egrep` is deprecated on some systems.

### Syntax

```bash
grep -E "PATTERN" FILE
egrep "PATTERN" FILE
```

### Common extended regular-expression operators

| Pattern | Meaning |
| --- | --- |
| `a | b` |
| `+` | Match one or more occurrences |
| `?` | Match zero or one occurrence |
| `{n}` | Match exactly `n` occurrences |
| `{n,m}` | Match between `n` and `m` occurrences |
| `()` | Group expressions |
| `^` | Start of line |
| `$` | End of line |
| `.` | Any single character |
| `[abc]` | One character from `a`, `b`, or `c` |
| `[^abc]` | Any character except `a`, `b`, or `c` |

### Examples

```bash
# Search for either "error" or "warning"
grep -E "error|warning" app.log

# Search for HTTP 4xx or 5xx status codes
grep -E "HTTP/[0-9.]+ [45][0-9]{2}" access.log

# Find lines containing a number
grep -E "[0-9]+" data.txt

# Find common email-shaped strings
grep -E "[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}" users.txt

# Find lines beginning with ERROR or WARNING
grep -E "^(ERROR|WARNING)" app.log
```

> For complex patterns, use `grep -E` instead of the legacy `egrep` command.

---

## 3. `sed`

`sed` means **stream editor**. It processes text line by line and is commonly used for substitution, deletion, printing, and filtering.

### Syntax

```bash
sed [OPTIONS] 'COMMAND' FILE
```

### Substitution

```bash
# Replace the first occurrence of "old" with "new" on each line
sed 's/old/new/' file.txt

# Replace every occurrence on each line
sed 's/old/new/g' file.txt

# Modify the file in place on Linux
sed -i 's/old/new/g' file.txt

# Modify the file in place on macOS
sed -i '' 's/old/new/g' file.txt
```

### Other useful commands

```bash
# Print lines 1 through 5
sed -n '1,5p' file.txt

# Print only line 10
sed -n '10p' file.txt

# Delete blank lines
sed '/^$/d' file.txt

# Delete lines containing "DEBUG"
sed '/DEBUG/d' app.log

# Remove leading whitespace
sed 's/^[[:space:]]*//' file.txt

# Remove trailing whitespace
sed 's/[[:space:]]*$//' file.txt

# Add a prefix to every line
sed 's/^/INFO: /' file.txt
```

### Common `sed` commands

| Command | Meaning |
| --- | --- |
| `s/old/new/` | Substitute text |
| `d` | Delete a line |
| `p` | Print a line |
| `q` | Quit after the current line |
| `-n` | Suppress default output |
| `-i` | Edit the file in place |

> Always make a backup before using `sed -i` on important files:```bash
sed -i.bak 's/old/new/g' file.txt
```

---

## 4. `awk`

`awk` is a text-processing language designed for reading columns, filtering records, performing calculations, and generating reports.

### Syntax

```bash
awk 'PATTERN { ACTION }' FILE
```

### Built-in fields and variables

| Variable | Meaning |
| --- | --- |
| `$0` | Entire current line |
| `$1`, `$2`, ... | First, second, and later fields |
| `NF` | Number of fields in the current line |
| `NR` | Current record/line number |
| `FNR` | Line number within the current file |
| `FS` | Input field separator |
| `OFS` | Output field separator |
| `BEGIN` | Runs before reading input |
| `END` | Runs after all input is read |

### Examples

```bash
# Print the first column
awk '{print $1}' file.txt

# Print the first and third columns
awk '{print $1, $3}' file.txt

# Use comma as the field separator
awk -F',' '{print $1, $3}' users.csv

# Print line number and complete line
awk '{print NR, $0}' file.txt

# Print lines where the third column is greater than 50
awk '$3 > 50 {print $0}' data.txt

# Print the last field on each line
awk '{print $NF}' file.txt

# Calculate the sum of the second column
awk '{sum += $2} END {print sum}' numbers.txt

# Print a formatted report
awk 'BEGIN {printf "%-15s %s\n", "NAME", "SCORE"} {printf "%-15s %s\n", $1, $2}' scores.txt
```

### Working with CSV-like data

```bash
# Print name and email from a comma-separated file
awk -F',' 'NR > 1 {print $1, $3}' users.csv
```

> Simple `awk -F','` parsing is not sufficient for CSV files containing quoted commas. Use a CSV-aware tool such as Python for complex CSV data.

---

## 5. `cut`

`cut` extracts sections, columns, or character ranges from each line of a file.

### Syntax

```bash
cut OPTION... [FILE]
```

### Examples

```bash
# Extract the first field separated by a colon
cut -d':' -f1 /etc/passwd

# Extract fields 1 and 3 from a comma-separated file
cut -d',' -f1,3 users.csv

# Extract fields 2 through 4
cut -d',' -f2-4 users.csv

# Extract characters 1 through 10
cut -c1-10 file.txt

# Extract the first character from each line
cut -c1 file.txt

# Extract everything from character 5 onward
cut -c5- file.txt
```

### Common options

| Option | Meaning |
| --- | --- |
| `-d DELIMITER` | Set the field delimiter |
| `-f LIST` | Select fields |
| `-c LIST` | Select character positions |
| `-b LIST` | Select byte positions |
| `--complement` | Select everything except the specified fields/characters |
| `-s` | Suppress lines without the delimiter |

---

## 6. `sort`

`sort` sorts lines of text alphabetically, numerically, by key, or in reverse order.

### Syntax

```bash
sort [OPTIONS] [FILE]
```

### Examples

```bash
# Alphabetical sort
sort names.txt

# Reverse alphabetical sort
sort -r names.txt

# Numeric sort
sort -n numbers.txt

# Human-readable numeric sort, such as 2K, 10M, and 1G
sort -h sizes.txt

# Sort and remove duplicate lines
sort -u names.txt

# Sort by the second whitespace-separated column
sort -k2 data.txt

# Sort by the second column numerically
sort -k2,2n scores.txt

# Sort a comma-separated file by column 3
sort -t',' -k3,3n data.csv
```

### Common options

| Option | Meaning |
| --- | --- |
| `-r` | Reverse order |
| `-n` | Numeric sort |
| `-h` | Human-readable numeric sort |
| `-f` | Ignore case |
| `-u` | Unique output |
| `-k FIELD` | Sort using a field/key |
| `-t CHAR` | Set field delimiter |
| `-o FILE` | Write output to a file |
| `-c` | Check whether input is sorted |

---

## 7. `uniq`

`uniq` reports or removes **adjacent** duplicate lines. Because it only compares neighboring lines, use `sort` first when duplicates may be separated.

### Syntax

```bash
uniq [OPTIONS] [INPUT] [OUTPUT]
```

### Examples

```bash
# Remove adjacent duplicate lines
uniq names.txt

# Sort first, then remove all duplicates
sort names.txt | uniq

# Short form of sort plus uniq
sort -u names.txt

# Count occurrences of each line
sort names.txt | uniq -c

# Show only duplicate lines
sort names.txt | uniq -d

# Show only lines that occur once
sort names.txt | uniq -u

# Ignore the first two fields when comparing
uniq -f 2 data.txt
```

### Common options

| Option | Meaning |
| --- | --- |
| `-c` | Prefix each line with its count |
| `-d` | Print only duplicated lines |
| `-u` | Print only unique lines |
| `-i` | Ignore case |
| `-f N` | Skip the first `N` fields |
| `-s N` | Skip the first `N` characters |

---

## 8. `wc`

`wc` counts lines, words, characters, and bytes.

### Syntax

```bash
wc [OPTIONS] [FILE]
```

### Examples

```bash
# Show lines, words, and bytes
wc file.txt

# Count lines only
wc -l file.txt

# Count words only
wc -w file.txt

# Count characters
wc -m file.txt

# Count bytes
wc -c file.txt

# Count files in a directory
find . -maxdepth 1 -type f | wc -l

# Count matching lines
 grep -c "ERROR" app.log
```

### Common options

| Option | Meaning |
| --- | --- |
| `-l` | Lines |
| `-w` | Words |
| `-m` | Characters |
| `-c` | Bytes |
| `-L` | Length of the longest line |

> A space before `grep` in the final example is harmless in interactive Bash but should be removed in scripts for clarity.

---

## 9. `tr`

`tr` translates, replaces, squeezes, or deletes characters from standard input. It does not normally edit files directly; use input redirection or a pipeline.

### Syntax

```bash
tr [OPTIONS] SET1 [SET2]
```

### Examples

```bash
# Convert lowercase letters to uppercase
printf 'hello world\n' | tr 'a-z' 'A-Z'

# Convert uppercase letters to lowercase
printf 'HELLO WORLD\n' | tr 'A-Z' 'a-z'

# Replace spaces with underscores
printf 'hello world\n' | tr ' ' '_'

# Delete all digits
printf 'abc123\n' | tr -d '0-9'

# Squeeze repeated spaces into one space
printf 'many    spaces\n' | tr -s ' '

# Convert Windows carriage returns to nothing
tr -d '\r' < windows.txt > unix.txt

# Replace newlines with spaces
tr '\n' ' ' < file.txt
```

### Common options

| Option | Meaning |
| --- | --- |
| `-d` | Delete characters in SET1 |
| `-s` | Squeeze repeated characters |
| `-c` | Use the complement of SET1 |
| `-t` | Translate only the length of SET2 |

---

## 10. `tee`

`tee` reads from standard input and writes the same data both to the terminal and to one or more files.

### Syntax

```bash
COMMAND | tee [OPTIONS] FILE...
```

### Examples

```bash
# Display output and save it to a file
ls -l | tee listing.txt

# Append instead of overwriting
ls -l | tee -a listing.txt

# Save output from a command while still seeing it
./build.sh 2>&1 | tee build.log

# Write to multiple files
whoami | tee user1.txt user2.txt

# Use tee with sudo to write a protected file
printf 'server.example.com\n' | sudo tee -a /etc/hosts
```

### Common options

| Option | Meaning |
| --- | --- |
| `-a` | Append to files instead of overwriting |
| `-i` | Ignore interrupts |

> `sudo echo "text" > /protected/file` usually fails because the shell performs the redirection before `sudo`. Use `sudo tee` instead.

---

## 11. `xargs`

`xargs` builds and runs commands using items read from standard input. It is useful for applying one command to many files or arguments.

### Syntax

```bash
COMMAND_PRODUCING_INPUT | xargs [OPTIONS] COMMAND
```

### Examples

```bash
# Remove files listed in files.txt
xargs rm < files.txt

# Search for "TODO" in all .txt files found by find
find . -name '*.txt' -print0 | xargs -0 grep -n "TODO"

# Run a command once per input item
printf 'one\ntwo\nthree\n' | xargs -n1 echo "Item:"

# Pass several files to one command at a time
find . -name '*.log' -print0 | xargs -0 -n10 gzip

# Use a placeholder for each input item
printf 'a\nb\nc\n' | xargs -I{} sh -c 'echo "Processing {}"'

# Run commands in parallel with four workers
cat urls.txt | xargs -n1 -P4 curl -O
```

### Important options

| Option | Meaning |
| --- | --- |
| `-n N` | Use at most `N` arguments per command |
| `-I REPLACE` | Replace a placeholder with each input item |
| `-0` | Read NUL-separated input; use with `find -print0` |
| `-P N` | Run up to `N` commands in parallel |
| `-t` | Print commands before running them |
| `-r` | Do not run the command if input is empty; GNU systems |

### Safe filename handling

Always use `find -print0` with `xargs -0` when filenames may contain spaces, quotes, or newlines:

```bash
find . -type f -name '*.tmp' -print0 | xargs -0 rm --
```

For simple cases, `find` can execute the command directly:

```bash
find . -type f -name '*.tmp' -delete
```

---

## 12. `crontab`

`crontab` manages scheduled recurring jobs. A cron job runs commands automatically at specified times or intervals.

### Syntax

```bash
crontab [OPTIONS]
```

### Edit the current user's crontab

```bash
crontab -e
```

### Cron format

Each job has five time fields followed by the command:

```
MINUTE HOUR DAY_OF_MONTH MONTH DAY_OF_WEEK COMMAND
```

| Field | Allowed values |
| --- | --- |
| Minute | `0–59` |
| Hour | `0–23` |
| Day of month | `1–31` |
| Month | `1–12` or names such as `jan` |
| Day of week | `0–7` or names such as `mon`; Sunday is `0` or `7` |

### Cron operators

| Operator | Meaning | Example |
| --- | --- | --- |
| `*` | Every value | `* * * * *` every minute |
| `,` | List of values | `1,15,30` |
| `-` | Range | `9-17` |
| `/` | Step interval | `*/15` every 15 units |

### Examples

```
# Run every minute
* * * * * /path/to/script.sh

# Run every day at 2:30 AM
30 2 * * * /path/to/backup.sh

# Run every Monday at 9:00 AM
0 9 * * 1 /path/to/weekly-report.sh

# Run every 15 minutes
*/15 * * * * /path/to/check.sh

# Run at 6:00 PM on weekdays
0 18 * * 1-5 /path/to/workday.sh

# Run on the first day of every month at midnight
0 0 1 * * /path/to/monthly.sh
```

### Redirect output to a log

```
0 2 * * * /home/user/backup.sh >> /home/user/backup.log 2>&1
```

### Set environment variables

```
SHELL=/bin/bash
PATH=/usr/local/bin:/usr/bin:/bin

0 2 * * * /home/user/backup.sh
```

### Manage another user's crontab

```bash
sudo crontab -u username -e
```

> Use absolute paths in cron jobs. Cron runs with a limited environment and may not use the same `PATH` as your interactive shell.

---

## 13. `crontab -l`

`crontab -l` lists the current user's scheduled cron jobs.

### Examples

```bash
# List your cron jobs
crontab -l

# List another user's cron jobs as root
sudo crontab -u username -l

# Safely check whether a crontab exists
crontab -l 2>/dev/null || echo "No crontab installed"

# Back up the current crontab
crontab -l > crontab.backup
```

### Restore a crontab backup

```bash
crontab crontab.backup
```

To remove all cron jobs for the current user:

```bash
crontab -r
```

> `crontab -r` removes the entire crontab without the normal editor step. Use it carefully.

---

## 14. `at`

`at` schedules a command to run **once** at a specified time. Unlike `cron`, it is not recurring.

### Syntax

```bash
at TIME
```

### Examples

```bash
# Run a command at 10:00 PM
at 10:00 PM

# Run tomorrow at 9:30 AM
at 9:30 AM tomorrow

# Run in one hour
at now + 1 hour

# Run in 30 minutes
at now + 30 minutes

# Run at a specific date and time
at 10:00 AM 12/25/2026
```

After entering `at TIME`, type the commands and press **Ctrl+D** to submit:

```
$ at now + 10 minutes
at> /home/user/backup.sh
at> <Ctrl+D>
```

### Schedule a command non-interactively

```bash
echo "/home/user/backup.sh" | at 11:00 PM

at now + 5 minutes < /home/user/job.sh
```

### Manage one-time jobs

```bash
# List pending jobs
atq

# Remove a pending job by job ID
atrm JOB_ID
```

### Common time expressions

```bash
at midnight
at noon
at teatime
at 5 PM today
at 5 PM tomorrow
at now + 2 days
at 08:00 10/31/2026
```

> The `atd` service must be running, and your user account must be permitted to use `at`.

---

## 15. `watch`

`watch` repeatedly runs a command and displays its output. It is useful for monitoring files, processes, disk usage, and system activity.

### Syntax

```bash
watch [OPTIONS] COMMAND
```

### Examples

```bash
# Run a command every two seconds
watch date

# Monitor disk usage every five seconds
watch -n 5 df -h

# Monitor a directory listing
watch -n 1 'ls -lh /var/log'

# Monitor running processes
watch -n 2 'ps aux --sort=-%cpu | head'

# Highlight differences between updates
watch -d 'free -h'

# Stop when the command exits successfully
watch -g 'test -f /tmp/complete'
```

Press **Ctrl+C** to stop `watch`.

### Common options

| Option | Meaning |
| --- | --- |
| `-n SECONDS` | Set update interval |
| `-d` | Highlight differences between updates |
| `-g` | Exit when output changes |
| `-t` | Hide the title/header |
| `-b` | Beep if the command exits with a non-zero status |
| `-e` | Exit if the command has an error |

> Quote commands containing pipes, redirects, variables, or multiple shell operations:```bash
watch -n 2 'df -h | grep -v tmpfs'
```

---

## 16. Useful Pipelines

Linux commands become especially powerful when connected with pipes (`|`). The output of one command becomes the input of the next.

### Find the most common words in a file

```bash
tr -cs '[:alnum:]' '\n' < file.txt | tr '[:upper:]' '[:lower:]' | sort | uniq -c | sort -nr | head
```

### Find the most common IP addresses in a web log

```bash
awk '{print $1}' access.log | sort | uniq -c | sort -nr | head -10
```

### Count HTTP status codes

```bash
awk '{print $9}' access.log | sort | uniq -c | sort -nr
```

### Find the largest files

```bash
find . -type f -printf '%s %p\n' | sort -nr | head -10
```

### Search source code for TODO and FIXME markers

```bash
grep -RInE 'TODO|FIXME' --exclude-dir=.git .
```

### Monitor an application log

```bash
watch -n 2 'tail -n 20 /var/log/app.log'
```

### Save and display a deployment log

```bash
./deploy.sh 2>&1 | tee "deploy-$(date +%Y%m%d-%H%M%S).log"
```

### Extract unique email addresses from text

```bash
grep -Eo '[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}' file.txt | sort -fu
```

### List files changed recently

```bash
find . -type f -mmin -60 -print
```

---

## 17. Important Safety Notes

1. **Quote filenames and variables** when they may contain spaces or special characters:

   ```bash
   rm -- "$filename"
   ```

1. **Preview destructive commands first:**

   ```bash
   find . -name '*.tmp' -print
   ```

   Only then replace `-print` with `-delete` if the result is correct.

1. **Back up before in-place edits:**

   ```bash
   sed -i.bak 's/old/new/g' file.txt
   ```

1. **Use ****`--`**** before filenames** when a filename may begin with a hyphen:

   ```bash
   rm -- -strange-filename
   ```

1. **Use NUL-safe pipelines** for arbitrary filenames:

   ```bash
   find . -type f -print0 | xargs -0 -n1 printf '%s\n'
   ```

1. **Be careful with elevated privileges.** Verify commands before using `sudo`, especially with `rm`, `sed -i`, `xargs`, and redirections.

1. **Use absolute paths in cron and ****`at`**** jobs.** The scheduled environment is different from your interactive terminal.

1. **Do not expose secrets** in command history, scripts, cron entries, or logs. Prefer protected environment files or a secrets manager.

1. **Check scheduled tasks regularly:**

   ```bash
   crontab -l
   atq
   ```

1. **Read the manual page for system-specific behavior:**

   ```bash
   man grep
   man sed
   man awk
   man crontab
   ```

---

## Quick Command Summary

| Command | Main purpose |
| --- | --- |
| `grep` | Search text patterns |
| `grep -E` / `egrep` | Search using extended regular expressions |
| `sed` | Stream editing and substitution |
| `awk` | Column processing and text reports |
| `cut` | Extract columns or characters |
| `sort` | Sort lines |
| `uniq` | Report or remove adjacent duplicates |
| `wc` | Count lines, words, and characters |
| `tr` | Translate, delete, or squeeze characters |
| `tee` | Display and save command output |
| `xargs` | Build commands from standard input |
| `crontab` | Schedule recurring jobs |
| `crontab -l` | List recurring jobs |
| `at` | Schedule a one-time job |
| `watch` | Repeatedly monitor a command |