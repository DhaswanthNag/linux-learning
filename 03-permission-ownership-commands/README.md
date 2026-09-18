# 🔐 Linux Permissions & Ownership Commands

> Beginner-friendly reference for managing file permissions and ownership in Linux.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `ls -l` | View permissions and ownership | `ls -l` |
| `chmod` | Change permissions | `chmod 755 file.sh` |
| `chmod +x` | Make a file executable | `chmod +x script.sh` |
| `chown` | Change file owner | `sudo chown user file.txt` |
| `chgrp` | Change group owner | `sudo chgrp devs file.txt` |
| `chown -R` | Change ownership recursively | `sudo chown -R user mydir/` |
| `chmod -R` | Change permissions recursively | `chmod -R 755 mydir/` |

---

## 🔎 1. `ls -l` — View Permissions

```bash
ls -l
```

Example:

```text
-rwxr-xr-- 1 user user file.txt
```

### Permission Structure

```text
-rwxr-xr--
 │   │  │
 │   │  └── Others
 │   └───── Group
 └───────── Owner
```

- `r` → Read
- `w` → Write
- `x` → Execute
- `-` → No permission

---

## 🔑 2. `chmod` — Change Permissions

```bash
chmod 755 file.sh
```

### Permission Values

| Number | Permission |
|---|---|
| `0` | None |
| `1` | Execute |
| `2` | Write |
| `4` | Read |
| `5` | Read + Execute |
| `6` | Read + Write |
| `7` | Read + Write + Execute |

Example:

```text
755 = rwxr-xr-x
```

---

## ▶️ 3. `chmod +x` — Make Executable

```bash
chmod +x script.sh
```

Run the script:

```bash
./script.sh
```

---

## 👤 4. `chown` — Change Owner

```bash
sudo chown newuser file.txt
```

Change owner and group:

```bash
sudo chown newuser:devs file.txt
```

---

## 👥 5. `chgrp` — Change Group

```bash
sudo chgrp devs file.txt
```

---

## 🔄 6. `chown -R` — Change Ownership Recursively

```bash
sudo chown -R newuser mydir/
```

> ⚠️ `-R` affects the directory and everything inside it.

---

## 🔁 7. `chmod -R` — Change Permissions Recursively

```bash
chmod -R 755 mydir/
```

> ⚠️ Be careful when changing permissions recursively.

---

## 🧪 Mini Practice

```bash
mkdir permissions-practice

cd permissions-practice

touch file.txt

ls -l

chmod 644 file.txt

ls -l

chmod +x file.txt

ls -l

cd ..
```

---

## 🛡️ Safety Tips

- Always check permissions with `ls -l`.
- Be careful with `sudo`.
- Be careful with `chmod -R` and `chown -R`.
- Avoid unnecessary `777` permissions.
- Test commands in a practice directory first.

---

## 📚 References

- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)
- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Bash Reference](https://www.gnu.org/software/bash/manual/bash.html)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️