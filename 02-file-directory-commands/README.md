# 📁 Linux File & Directory Commands

> A beginner-friendly reference for creating, viewing, copying, moving, deleting, and searching files and directories.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `touch` | Create a file | `touch file.txt` |
| `cat` | Display file contents | `cat file.txt` |
| `mkdir` | Create a directory | `mkdir newdir` |
| `cp` | Copy files/directories | `cp file.txt copy.txt` |
| `mv` | Move/rename files | `mv file.txt new.txt` |
| `rm` | Delete a file | `rm file.txt` |
| `rm -r` | Delete a directory | `rm -r mydir` |
| `find` | Search files/directories | `find . -name file.txt` |
| `tree` | Show directory structure | `tree` |
| `locate` | Find files using database | `locate file.txt` |

---

## 📝 1. `touch` — Create a File

```bash
touch file.txt
```

Create multiple files:

```bash
touch file1.txt file2.txt
```

---

## 📖 2. `cat` — Display File Contents

```bash
cat file.txt
```

Create/write a file:

```bash
cat > greeting.txt
```

Press `Ctrl + D` when finished.

---

## 📂 3. `mkdir` — Create a Directory

```bash
mkdir newdir
```

Create nested directories:

```bash
mkdir -p projects/linux/commands
```

---

## 📋 4. `cp` — Copy Files/Directories

Copy a file:

```bash
cp file.txt copy.txt
```

Copy a directory:

```bash
cp -r mydir backup/
```

---

## 🚚 5. `mv` — Move or Rename

Rename:

```bash
mv file.txt new.txt
```

Move:

```bash
mv file.txt Documents/
```

---

## 🗑️ 6. `rm` — Delete a File

```bash
rm file.txt
```

Ask for confirmation:

```bash
rm -i file.txt
```

> ⚠️ `rm` normally does not move files to Trash.

---

## 🗑️ 7. `rm -r` — Delete Directory

```bash
rm -r mydir
```

Ask before deleting:

```bash
rm -ri mydir
```

> 🚨 Be very careful with recursive deletion.

---

## 🔎 8. `find` — Search Files

Search by name:

```bash
find . -name "file.txt"
```

Find files:

```bash
find . -type f -name "*.txt"
```

Find directories:

```bash
find . -type d -name "Documents"
```

---

## 🌳 9. `tree` — Show Directory Structure

```bash
tree
```

Install on Ubuntu if needed:

```bash
sudo apt install tree
```

---

## 🔍 10. `locate` — Find Files Quickly

```bash
locate file.txt
```

Update the database:

```bash
sudo updatedb
```

> `locate` is usually faster than `find`, but its database may need updating.

---

## ⚡ `find` vs `locate`

| Feature | `find` | `locate` |
|---|---|---|
| Method | Searches filesystem | Searches database |
| Speed | Usually slower | Usually faster |
| New files | Finds immediately | May need `updatedb` |
| Complex searches | Yes | Limited |

---

## 🧪 Mini Practice

```bash
mkdir linux-files

cd linux-files

touch file.txt

echo "Hello Linux" > file.txt

cat file.txt

cp file.txt copy.txt

mv copy.txt renamed.txt

mkdir backup

cp renamed.txt backup/

find . -name "file.txt"

tree

cd ..
```

---

## 🛡️ Safety Tips

- Check your location with `pwd`.
- Use `ls` before deleting files.
- Be careful with `rm` and `rm -r`.
- Avoid `rm -rf` unless you fully understand the target.
- Double-check paths before destructive commands.
- Use `cp` to create backups before important changes.

---

## 📌 Quick Revision

```text
touch   → Create file
cat     → Read file
mkdir   → Create directory
cp      → Copy
mv      → Move / Rename
rm      → Delete file
rm -r   → Delete directory
find    → Search filesystem
tree    → Show directory tree
locate  → Search database
```

---

## 📚 References

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Bash Reference](https://www.gnu.org/software/bash/manual/bash.html)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️