# 🐧 Linux Basic Commands

> A beginner-friendly reference for essential Linux terminal commands. Use these commands to navigate your system, inspect files, display information, and control your terminal.

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `pwd` | Shows the current directory | `pwd` |
| `ls` | Lists files and directories | `ls` |
| `cd` | Changes the current directory | `cd Documents` |
| `clear` | Clears the terminal screen | `clear` |
| `echo` | Prints text or values | `echo "Hello Linux"` |
| `whoami` | Shows the current username | `whoami` |
| `date` | Displays the current date and time | `date` |
| `man` | Opens a command's manual page | `man ls` |
| `history` | Displays previously used commands | `history` |
| `exit` | Closes the terminal session | `exit` |

---

## 🧭 1. `pwd` — Print Working Directory

The `pwd` command shows the full path of the directory you are currently working in.

```bash
pwd
```

Example output:

```text
/home/user
```

✅ **Use it when:** You want to know your current location in the filesystem.

---

## 📁 2. `ls` — List Files and Directories

The `ls` command displays the files and directories inside the current directory.

```bash
ls
```

Example output:

```text
file1.txt  Documents  Images
```

### Useful options

```bash
ls -l       # Show detailed information
ls -a       # Include hidden files
ls -lh      # Show readable file sizes
ls -la      # Show hidden files with detailed information
```

✅ **Use it when:** You want to inspect the contents of a directory.

---

## 📂 3. `cd` — Change Directory

The `cd` command moves you from one directory to another.

```bash
cd Documents
pwd
```

Example output:

```text
/home/user/Documents
```

### Common navigation examples

```bash
cd ..       # Move to the parent directory
cd ~        # Move to your home directory
cd /        # Move to the filesystem root
cd -        # Return to the previous directory
```

✅ **Use it when:** You need to navigate through folders.

---

## 🧹 4. `clear` — Clear the Terminal

The `clear` command removes previous output from the visible terminal screen.

```bash
clear
```

> ℹ️ This command does not delete files or erase your command history. It only refreshes the visible screen.

✅ **Use it when:** The terminal becomes crowded and you want a clean workspace.

---

## 🖨️ 5. `echo` — Print Text or Values

The `echo` command prints text, variables, or other values in the terminal.

```bash
echo "Hello Linux"
```

Output:

```text
Hello Linux
```

### More examples

```bash
echo $HOME                 # Print the home directory
echo "Linux is powerful"    # Print a sentence
echo "Hello" > greeting.txt # Write text to a file
```

> ⚠️ The redirection example `>` overwrites the file if it already exists. Use `>>` to append text instead.

✅ **Use it when:** You want to display information or send text to another command or file.

---

## 👤 6. `whoami` — Show the Current User

The `whoami` command prints the username of the account currently running the terminal session.

```bash
whoami
```

Example output:

```text
user
```

✅ **Use it when:** You need to confirm which user account is active.

---

## 🕒 7. `date` — Show Date and Time

The `date` command displays the system's current date and time.

```bash
date
```

Example output:

```text
Sat May 24 10:30:45 AM UTC 2025
```

### Formatting examples

```bash
date +%Y-%m-%d       # Example: 2025-05-24
date +%H:%M:%S       # Example: 10:30:45
```

✅ **Use it when:** You need the current system time or a formatted date for a script.

---

## 📖 8. `man` — Read Manual Pages

The `man` command opens the official manual page for a command.

```bash
man ls
```

Inside a manual page:

- Press **Space** to move down one page.
- Press **b** to move back one page.
- Press **/** and enter a word to search.
- Press **q** to quit.

You can also use:

```bash
man pwd
man cd
man echo
```

✅ **Use it when:** You need detailed documentation, options, or syntax for a command.

---

## 🧾 9. `history` — View Command History

The `history` command lists commands previously entered in the terminal.

```bash
history
```

Example output:

```text
1  pwd
2  ls
3  cd Documents
4  history
```

### Reuse a previous command

```bash
!!       # Run the previous command again
!3       # Run command number 3 from the history
history  # Display the command history
```

> 🔐 Avoid storing passwords or other sensitive information in command arguments. Shell history may save them.

✅ **Use it when:** You want to find or repeat a command you used earlier.

---

## 🚪 10. `exit` — Close the Terminal Session

The `exit` command ends the current shell or terminal session.

```bash
exit
```

You can also press:

```text
Ctrl + D
```

✅ **Use it when:** You have finished working and want to close the shell.

---

## ⌨️ Helpful Terminal Shortcuts

| Shortcut | Action |
|---|---|
| `Tab` | Auto-complete commands, filenames, and directory names |
| `↑` / `↓` | Move through previously entered commands |
| `Ctrl + C` | Stop the currently running command |
| `Ctrl + L` | Clear the terminal screen |
| `Ctrl + D` | Exit the current shell or send end-of-file input |

### Example: Fast navigation with `Tab`

Instead of typing a long directory name, type the first few characters and press **Tab**:

```bash
cd Doc<Tab>
```

The shell may complete it as:

```bash
cd Documents
```

---

## 🧪 Mini Practice Session

Try these commands in order:

```bash
pwd
ls
mkdir -p linux-practice
cd linux-practice
echo "Linux practice" > notes.txt
ls
cat notes.txt
cd ..
pwd
```

This exercise shows your location, lists files, creates a practice directory, writes a text file, reads it, and returns to the parent directory.

> ⚠️ The practice session includes `mkdir` and `cat` to make the example useful. These commands are not part of the original image, but they are standard commands commonly used with the commands above.

---

## 🛡️ Safety Tips

1. Check your location with `pwd` before creating, moving, or deleting files.
2. Use `ls` to inspect a directory before running other commands in it.
3. Read a command's manual page with `man command` when you are unsure about an option.
4. Be careful with redirection operators such as `>` because they can overwrite files.
5. Do not run commands copied from the internet unless you understand what they do.

---

## 📚 References

[1]: https://www.gnu.org/software/coreutils/manual/coreutils.html "GNU Coreutils Manual"
[2]: https://man7.org/linux/man-pages/ "Linux man-pages Project"
[3]: https://www.gnu.org/software/bash/manual/bash.html "GNU Bash Reference Manual"

⭐ If this guide helped you learn Linux commands, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️

## 🔗 Further Reading

See the [GNU Coreutils Manual][1], the [Linux man-pages Project][2], and the [GNU Bash Reference Manual][3] for authoritative documentation.

---

_This README is based on the commands shown in the provided Linux basic commands reference image._
