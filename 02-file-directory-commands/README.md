# 📁 Linux File & Directory Commands

> A beginner-friendly reference for managing files and directories efficiently in Linux. These commands help you create, view, copy, move, delete, and search for files and directories.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `touch` | Creates a new empty file | `touch file.txt` |
| `cat` | Displays file contents | `cat file.txt` |
| `mkdir` | Creates a directory | `mkdir newdir` |
| `cp` | Copies files or directories | `cp file.txt copy.txt` |
| `mv` | Moves or renames files/directories | `mv file.txt new.txt` |
| `rm` | Deletes a file | `rm file.txt` |
| `rm -r` | Deletes a directory recursively | `rm -r mydir` |
| `find` | Searches for files or directories | `find / -name file.txt` |
| `tree` | Shows directory tree structure | `tree /home/user` |
| `locate` | Finds files using a database | `locate file.txt` |

---

## 📝 1. `touch` — Create a New File

The `touch` command creates a new empty file if the specified file does not already exist.

```bash
touch file.txt
```

Example:

```text
file.txt
```

### More Examples

```bash
touch notes.txt
touch test.txt
touch file1.txt file2.txt file3.txt
```

> ℹ️ If the file already exists, `touch` updates its access and modification timestamps instead of deleting or replacing its contents.

✅ **Use it when:** You want to quickly create an empty file.

---

## 📖 2. `cat` — Display File Contents

The `cat` command displays the contents of a file directly in the terminal.

```bash
cat file.txt
```

Example output:

```text
Hello Linux
```

### More Examples

```bash
cat notes.txt
cat file1.txt file2.txt
```

You can also use `cat` to create a file:

```bash
cat > greeting.txt
Hello Linux
```

Press **Ctrl + D** when finished.

> ℹ️ Be careful with `cat > file.txt` because it overwrites the existing contents of the file.

✅ **Use it when:** You want to quickly read the contents of a text file.

---

## 📂 3. `mkdir` — Create a Directory

The `mkdir` command creates a new directory.

```bash
mkdir newdir
```

Example:

```text
newdir/
```

### Create Multiple Directories

```bash
mkdir folder1 folder2 folder3
```

### Create Nested Directories

```bash
mkdir -p projects/linux/commands
```

The `-p` option creates parent directories when they do not already exist.

✅ **Use it when:** You want to create a new folder or directory structure.

---

## 📄 4. `cp` — Copy Files or Directories

The `cp` command copies files or directories from one location to another.

```bash
cp file.txt copy.txt
```

This creates a duplicate called `copy.txt`.

### Copy a File to Another Directory

```bash
cp file.txt Documents/
```

### Copy a Directory Recursively

```bash
cp -r mydir backup/
```

> ⚠️ Use `-r` when copying directories and their contents.

✅ **Use it when:** You want to create a copy or backup of a file or directory.

---

## 🚚 5. `mv` — Move or Rename Files/Directories

The `mv` command is used to move files or directories and also to rename them.

### Rename a File

```bash
mv file.txt new.txt
```

### Move a File

```bash
mv file.txt Documents/
```

### Move and Rename a File

```bash
mv file.txt Documents/new.txt
```

✅ **Use it when:** You want to move files between directories or rename them.

---

## 🗑️ 6. `rm` — Delete a File

The `rm` command removes files.

```bash
rm file.txt
```

After running this command, the file is removed.

### Remove Multiple Files

```bash
rm file1.txt file2.txt
```

### Ask for Confirmation

```bash
rm -i file.txt
```

> ⚠️ `rm` normally deletes files without moving them to the desktop Trash. Be careful before using it.

✅ **Use it when:** You want to remove unwanted files.

---

## 🗑️ 7. `rm -r` — Delete a Directory Recursively

The `rm -r` command removes a directory and everything inside it.

```bash
rm -r mydir
```

### Ask Before Deleting

```bash
rm -ri mydir
```

> 🚨 **Be extremely careful with recursive deletion.** Make sure you have the correct directory before running the command.

> ⚠️ Never use destructive commands such as `rm -rf` unless you fully understand what they will delete.

✅ **Use it when:** You need to remove a directory and its contents.

---

## 🔎 8. `find` — Search for Files or Directories

The `find` command searches for files and directories based on different conditions.

### Search by Name

```bash
find / -name file.txt
```

Example output:

```text
/home/user/file.txt
```

### Search from the Current Directory

```bash
find . -name file.txt
```

### Search for Directories

```bash
find . -type d -name Documents
```

### Search for Files

```bash
find . -type f -name "*.txt"
```

> ℹ️ Searching from `/` may produce permission-denied messages and can take longer because it searches a large part of the filesystem.

✅ **Use it when:** You need to locate files or directories on your system.

---

## 🌳 9. `tree` — Show Directory Structure

The `tree` command displays files and directories in a tree-like structure.

```bash
tree /home/user
```

Example:

```text
/home/user
├── Documents
│   ├── notes.txt
│   └── report.txt
├── Pictures
│   └── photo.jpg
└── Downloads
    └── file.zip
```

### Show the Current Directory

```bash
tree
```

> ℹ️ On some Linux distributions, `tree` may not be installed by default.

On Ubuntu, you can install it with:

```bash
sudo apt install tree
```

Then run:

```bash
tree
```

✅ **Use it when:** You want to visually understand the structure of directories and files.

---

## 🔍 10. `locate` — Find Files Using a Database

The `locate` command searches for files using a pre-built database.

```bash
locate file.txt
```

Example output:

```text
/home/user/file.txt
/home/user/Documents/file.txt
```

### Update the Locate Database

```bash
sudo updatedb
```

Then search again:

```bash
locate file.txt
```

> 💡 **Tip:** `locate` is generally faster than `find` because it searches a database instead of scanning the filesystem each time.

> ⚠️ The database may not contain very recently created files until it is updated.

✅ **Use it when:** You want to quickly search for files by name.

---

## ⚡ `find` vs `locate`

| Feature | `find` | `locate` |
|---|---|---|
| Search method | Searches the filesystem | Searches a database |
| Speed | Can be slower | Usually very fast |
| Finds newly created files | Yes | Only after database update |
| Supports complex conditions | Yes | More limited |
| Database required | No | Yes |

### Example

```bash
find . -name "file.txt"
```

vs.

```bash
locate file.txt
```

---

## 🧪 Mini Practice Session

Try these commands in order:

```bash
mkdir linux-files

cd linux-files

touch file.txt

echo "Hello Linux" > file.txt

cat file.txt

cp file.txt copy.txt

mv copy.txt renamed.txt

ls

mkdir backup

cp renamed.txt backup/

ls backup

cd ..

find . -name "file.txt"

tree linux-files
```

### What You Learn

This practice session helps you learn how to:

- 📂 Create a directory
- 📝 Create a file
- ✏️ Write content to a file
- 📖 Read file contents
- 📋 Copy a file
- 🚚 Rename a file
- 📁 Create a backup directory
- 📦 Copy files into another directory
- 🔎 Search for files
- 🌳 View directory structure

---

## 🛡️ Safety Tips

1. Check your location with `pwd` before modifying files.
2. Use `ls` to inspect files and directories before deleting them.
3. Be especially careful with `rm` and `rm -r`.
4. Avoid using `rm -rf` unless you completely understand the target path.
5. Use `cp` to create a backup before making important changes.
6. Remember that `mv` can overwrite an existing destination in some situations.
7. When using `find /`, be aware that the search can be large and may produce permission errors.
8. Remember that `locate` depends on its database, which may need updating.
9. Do not run commands copied from the internet unless you understand what they do.

---

## ⌨️ Helpful Terminal Shortcuts

| Shortcut | Action |
|---|---|
| `Tab` | Auto-complete filenames and directories |
| `↑` / `↓` | Navigate through command history |
| `Ctrl + C` | Stop the current command |
| `Ctrl + L` | Clear the terminal |
| `Ctrl + D` | Exit the current shell |

---

## 📚 References

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Linux man-pages Project](https://man7.org/linux/man-pages/)
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)

---

⭐ If this guide helped you learn Linux commands, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️

---

## 🔗 Further Reading

For detailed command documentation, see:

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Linux man-pages Project](https://man7.org/linux/man-pages/)
- [GNU Bash Reference Manual](https://www.gnu.org/software/bash/manual/bash.html)

---

*This README is based on the File & Directory Commands reference image.*