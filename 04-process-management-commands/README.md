# ⚙️ Linux Process Management Commands

> A beginner-friendly reference for viewing, monitoring, controlling, and managing processes in Linux.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `ps` | Displays running processes | `ps` |
| `ps aux` | Displays all running processes | `ps aux` |
| `top` | Real-time process monitoring | `top` |
| `htop` | Interactive process viewer | `htop` |
| `kill` | Terminates a process | `kill 1234` |
| `killall` | Kills processes by name | `killall firefox` |
| `pkill` | Kills processes by name/pattern | `pkill chrome` |
| `jobs` | Shows background jobs | `jobs` |
| `bg` | Resumes a job in background | `bg %1` |
| `fg` | Brings a job to foreground | `fg %1` |
| `nice` | Starts a process with priority | `nice -n 10 command` |
| `renice` | Changes process priority | `renice -n 10 -p 1234` |
| `nohup` | Runs a command after logout | `nohup command &` |

---

## 🔍 1. `ps` — Display Processes

Shows processes running in the current terminal.

```bash
ps
```

Example:

```text
PID   TTY   TIME     CMD
1234  pts/0 00:00:00 bash
```

---

## 📋 2. `ps aux` — Display All Processes

Shows detailed information about processes running on the system.

```bash
ps aux
```

Useful for finding:

- PID
- CPU usage
- Memory usage
- User
- Running command

---

## 📊 3. `top` — Real-Time Process Monitor

Displays running processes and system resource usage in real time.

```bash
top
```

Press:

```text
q
```

to quit.

---

## 📈 4. `htop` — Interactive Process Viewer

Provides an interactive and user-friendly process monitor.

```bash
htop
```

> ℹ️ If not installed on Ubuntu:

```bash
sudo apt install htop
```

Press:

```text
q
```

to quit.

---

## 🛑 5. `kill` — Terminate a Process

Terminates a process using its PID.

```bash
kill 1234
```

Force termination:

```bash
kill -9 1234
```

> ⚠️ Use `kill -9` only when a normal `kill` does not work.

---

## 💀 6. `killall` — Kill Processes by Name

Terminates processes using their name.

```bash
killall firefox
```

> ⚠️ This can terminate multiple processes with the same name.

---

## 🎯 7. `pkill` — Kill Processes by Name

Terminates processes based on their name or pattern.

```bash
pkill chrome
```

Useful when you don't know the PID.

---

## 📦 8. `jobs` — View Background Jobs

Displays jobs started from the current shell.

```bash
jobs
```

Example:

```text
[1]+ Running    sleep 100 &
```

---

## 🌙 9. `bg` — Run Job in Background

Resumes a stopped job in the background.

```bash
bg %1
```

---

## 🔙 10. `fg` — Bring Job to Foreground

Brings a background job back to the foreground.

```bash
fg %1
```

---

## ⚡ 11. `nice` — Start with Process Priority

Starts a process with a specified priority.

```bash
nice -n 10 command
```

Higher nice values generally mean lower CPU priority.

---

## 🔧 12. `renice` — Change Process Priority

Changes the priority of an already running process.

```bash
renice -n 10 -p 1234
```

Here:

- `10` → New nice value
- `1234` → Process ID

---

## 🔌 13. `nohup` — Keep Process Running After Logout

Runs a command so it can continue after the terminal session ends.

```bash
nohup command &
```

Example:

```bash
nohup python3 app.py &
```

Output is commonly written to:

```text
nohup.out
```

---

## 🧪 Mini Practice

```bash
sleep 100 &

jobs

ps

ps aux

top

kill <PID>

jobs
```

### Useful Flow

```text
ps / ps aux
      ↓
Find the process
      ↓
Get the PID
      ↓
kill PID
      ↓
Stop the process
```

---

## 🛡️ Safety Tips

- Check the PID before using `kill`.
- Be careful with `kill -9`.
- `killall` and `pkill` can affect multiple processes.
- Don't terminate system processes unless you understand their purpose.
- Use `top` or `htop` to inspect processes before stopping them.

---

## ⌨️ Helpful Shortcuts

| Shortcut | Action |
|---|---|
| `Ctrl + C` | Stop the foreground process |
| `Ctrl + Z` | Suspend the foreground process |
| `bg` | Continue a stopped job in background |
| `fg` | Bring a background job to foreground |
| `q` | Quit `top` / `htop` |

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [GNU Bash Reference](https://www.gnu.org/software/bash/manual/bash.html)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️