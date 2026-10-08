# 🛠️ Linux Text Processing & Automation Commands

> A beginner-friendly reference for searching, filtering, processing text, managing output, scheduling jobs, and monitoring commands in Linux.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `grep` | Search for patterns in files | `grep "error" log.txt` |
| `egrep / grep -E` | Search using extended patterns | `grep -E "error|fail" log.txt` |
| `sed` | Filter and modify text | `sed 's/old/new/' file.txt` |
| `awk` | Process and analyze text | `awk '{print $1}' file.txt` |
| `cut` | Extract sections of lines | `cut -d',' -f1 file.csv` |
| `sort` | Sort lines of text | `sort names.txt` |
| `uniq` | Remove/report repeated lines | `uniq list.txt` |
| `wc` | Count lines, words, characters | `wc -l file.txt` |
| `tr` | Translate or replace characters | `tr 'a-z' 'A-Z'` |
| `tee` | Display and save output | `tee output.txt` |
| `xargs` | Build commands from input | `xargs rm` |
| `crontab -e` | Edit scheduled jobs | `crontab -e` |
| `crontab -l` | List scheduled jobs | `crontab -l` |
| `at` | Schedule a one-time job | `echo "date" \| at 10:00 PM` |
| `watch` | Run a command repeatedly | `watch -n 2 df -h` |

---

## 🔎 1. `grep` — Search for Text

`grep` searches files for lines matching a specified pattern.

```bash
grep "error" log.txt
```

Ignore case:

```bash
grep -i "error" log.txt
```

Show matching line numbers:

```bash
grep -n "error" log.txt
```

Search recursively:

```bash
grep -r "error" .
```

> 💡 `grep` is one of the most commonly used Linux commands for searching text.

---

## 🔍 2. `egrep` / `grep -E` — Extended Search

`grep -E` supports extended regular expressions for more advanced searches.

```bash
grep -E "error|fail" log.txt
```

This searches for either `error` or `fail`.

The older `egrep` command is equivalent to:

```bash
egrep "error|fail" log.txt
```

> 💡 Prefer `grep -E` in modern scripts.

---

## ✏️ 3. `sed` — Stream Editor

`sed` is used to search, filter, replace, and transform text.

Replace the first occurrence on each line:

```bash
sed 's/old/new/' file.txt
```

Replace all occurrences:

```bash
sed 's/old/new/g' file.txt
```

Delete a line:

```bash
sed '2d' file.txt
```

> 💡 `sed` normally prints modified output without changing the original file.

---

## 📊 4. `awk` — Text Processing

`awk` is useful for processing structured text and extracting columns.

Print the first column:

```bash
awk '{print $1}' file.txt
```

Print the first and second columns:

```bash
awk '{print $1, $2}' file.txt
```

Print a specific field from a CSV:

```bash
awk -F',' '{print $1}' file.csv
```

> 💡 `awk` is especially useful when working with columns and structured text.

---

## ✂️ 5. `cut` — Extract Text

`cut` extracts specific sections or columns from lines.

Extract the first field from a CSV:

```bash
cut -d',' -f1 file.csv
```

Extract characters:

```bash
cut -c1-5 file.txt
```

- `-d` → Field delimiter
- `-f` → Field number
- `-c` → Character position

---

## 🔤 6. `sort` — Sort Lines

Sorts lines alphabetically.

```bash
sort names.txt
```

Reverse order:

```bash
sort -r names.txt
```

Numeric sorting:

```bash
sort -n numbers.txt
```

---

## 🔁 7. `uniq` — Handle Duplicate Lines

`uniq` removes or reports consecutive duplicate lines.

```bash
uniq list.txt
```

Count repeated lines:

```bash
uniq -c list.txt
```

> ⚠️ For best results, sort the file first:

```bash
sort list.txt | uniq
```

---

## 🔢 8. `wc` — Count Text

`wc` counts lines, words, and characters.

Count lines:

```bash
wc -l file.txt
```

Count words:

```bash
wc -w file.txt
```

Count characters:

```bash
wc -m file.txt
```

Count everything:

```bash
wc file.txt
```

---

## 🔄 9. `tr` — Translate Characters

`tr` replaces or removes characters.

Convert lowercase to uppercase:

```bash
echo "hello" | tr 'a-z' 'A-Z'
```

Output:

```text
HELLO
```

Replace spaces with underscores:

```bash
echo "Hello Linux" | tr ' ' '_'
```

---

## 📺 10. `tee` — Display and Save Output

`tee` reads input and writes it to both the terminal and a file.

```bash
echo "Hello Linux" | tee output.txt
```

Append instead of overwrite:

```bash
echo "New line" | tee -a output.txt
```

> 💡 Useful when you want to see command output while saving it to a file.

---

## 🔗 11. `xargs` — Build Commands from Input

`xargs` converts input into command arguments.

Example:

```bash
cat files.txt | xargs ls
```

Remove files listed in a file:

```bash
cat files.txt | xargs rm
```

> ⚠️ Be careful when using `xargs` with destructive commands such as `rm`.

---

## ⏰ 12. `crontab -e` — Edit Scheduled Jobs

`crontab -e` opens your user's cron schedule for editing.

```bash
crontab -e
```

Example:

```text
0 10 * * * echo "Backup started"
```

Cron format:

```text
Minute Hour Day Month Weekday Command
```

Example:

```text
0 10 * * *
│  │
│  └── Hour
└───── Minute
```

> 💡 Cron is commonly used for automatically running recurring tasks.

---

## 📋 13. `crontab -l` — List Scheduled Jobs

Displays the current user's scheduled cron jobs.

```bash
crontab -l
```

Remove all cron jobs:

```bash
crontab -r
```

> ⚠️ Be careful with `crontab -r` because it removes the user's entire crontab.

---

## ⏱️ 14. `at` — Schedule a One-Time Job

`at` schedules a command to run once at a specified time.

```bash
echo "date" | at 10:00 PM
```

View scheduled jobs:

```bash
atq
```

Remove a scheduled job:

```bash
atrm JOB_ID
```

> 💡 Use `at` for one-time tasks and `cron` for recurring tasks.

---

## 👀 15. `watch` — Monitor a Command

`watch` repeatedly runs a command and displays its output.

```bash
watch df -h
```

Run every 2 seconds:

```bash
watch -n 2 df -h
```

> 💡 Useful for monitoring disk usage, processes, memory, or other changing system information.

---

## 🔗 Combining Commands with Pipes

Linux commands can be combined using the pipe `|`.

Example:

```bash
cat names.txt | sort | uniq
```

Another example:

```bash
ps aux | grep nginx
```

The output of one command becomes the input of the next command.

---

## 🧪 Mini Practice

Create a practice file:

```bash
echo -e "Linux\nLinux\nUbuntu\nLinux\nDocker" > names.txt
```

Search:

```bash
grep "Linux" names.txt
```

Sort:

```bash
sort names.txt
```

Remove duplicates:

```bash
sort names.txt | uniq
```

Count lines:

```bash
wc -l names.txt
```

Convert text:

```bash
echo "hello linux" | tr 'a-z' 'A-Z'
```

Save output:

```bash
sort names.txt | tee sorted.txt
```

Monitor disk usage:

```bash
watch -n 2 df -h
```

---

## 🛡️ Safety Tips

- Check files before using commands that modify them.
- Be careful with `sed -i` because it changes files directly.
- Double-check commands using `rm` with `xargs`.
- Understand cron jobs before scheduling them.
- Be careful with `crontab -r`.
- Use `sort | uniq` when you need to remove duplicates reliably.
- Test complex commands with sample files first.

---

## 📌 Quick Revision

```text
grep          → Search text
grep -E       → Extended pattern search
sed           → Edit/transform text
awk           → Process columns/data
cut           → Extract fields/characters
sort          → Sort lines
uniq          → Handle duplicate lines
wc            → Count lines/words/characters
tr            → Translate characters
tee           → Display and save output
xargs         → Build commands from input
crontab -e    → Edit scheduled jobs
crontab -l    → List scheduled jobs
at            → Schedule one-time job
watch         → Repeatedly run a command
```

---

## 🎯 When to Use These Commands

| Situation | Command |
|---|---|
| Search for text | `grep` |
| Search with patterns | `grep -E` |
| Replace text | `sed` |
| Process columns | `awk` |
| Extract fields | `cut` |
| Sort data | `sort` |
| Remove duplicates | `uniq` |
| Count lines/words | `wc` |
| Change characters | `tr` |
| Save command output | `tee` |
| Run commands from a list | `xargs` |
| Schedule recurring tasks | `crontab` |
| Schedule one-time tasks | `at` |
| Monitor changing output | `watch` |

---

## 📚 References

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [GNU Grep Manual](https://www.gnu.org/software/grep/manual/grep.html)
- [GNU Sed Manual](https://www.gnu.org/software/sed/manual/sed.html)
- [GNU Awk Manual](https://www.gnu.org/software/gawk/manual/gawk.html)
- [Linux man-pages](https://man7.org/linux/man-pages/)

---

⭐ If this guide helped you learn Linux commands, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️