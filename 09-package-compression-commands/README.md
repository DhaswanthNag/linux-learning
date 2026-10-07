# 📦 Linux Package & Compression Commands

> A beginner-friendly quick reference for managing packages, creating archives, and compressing files on Debian-based Linux systems.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `apt update` | Update package information | `sudo apt update` |
| `apt upgrade` | Upgrade installed packages | `sudo apt upgrade` |
| `apt install` | Install a package | `sudo apt install nginx` |
| `apt remove` | Remove a package | `sudo apt remove nginx` |
| `apt purge` | Remove package + configuration | `sudo apt purge nginx` |
| `apt search` | Search packages | `apt search nginx` |
| `dpkg -l` | List installed packages | `dpkg -l` |
| `tar -cvf` | Create TAR archive | `tar -cvf backup.tar folder/` |
| `tar -xvf` | Extract TAR archive | `tar -xvf backup.tar` |
| `gzip` | Compress a file | `gzip file.txt` |
| `gunzip` | Decompress `.gz` file | `gunzip file.txt.gz` |
| `zip` | Create ZIP archive | `zip backup.zip file.txt` |
| `unzip` | Extract ZIP archive | `unzip backup.zip` |

---

## 📦 Package Management

### 🔄 1. `apt update` — Update Package List

```bash
sudo apt update
```

Downloads the latest package information from configured repositories.

> 💡 It checks for available updates but does not install them.

---

### ⬆️ 2. `apt upgrade` — Upgrade Packages

```bash
sudo apt upgrade
```

Upgrades installed packages to newer available versions.

Common workflow:

```bash
sudo apt update
sudo apt upgrade
```

---

### 📥 3. `apt install` — Install Package

```bash
sudo apt install nginx
```

Installs a package and its required dependencies.

Multiple packages:

```bash
sudo apt install git curl wget
```

---

### 🗑️ 4. `apt remove` — Remove Package

```bash
sudo apt remove nginx
```

Removes the package while generally keeping package-managed configuration files.

---

### 🧹 5. `apt purge` — Remove Package & Configuration

```bash
sudo apt purge nginx
```

Removes the package and its package-managed configuration files.

> ⚠️ Use carefully because configuration files may be removed.

---

### 🔍 6. `apt search` — Search Packages

```bash
apt search nginx
```

Searches available repositories for matching packages.

---

### 📋 7. `dpkg -l` — List Installed Packages

```bash
dpkg -l
```

Lists installed Debian packages.

Search for a specific package:

```bash
dpkg -l | grep nginx
```

> 💡 `dpkg` is a lower-level Debian package management tool.

---

# 🗜️ Archive & Compression

### 📦 8. `tar -cvf` — Create TAR Archive

```bash
tar -cvf backup.tar my_folder/
```

Creates an archive without compression.

Options:

```text
-c → Create
-v → Verbose
-f → Filename
```

---

### 📂 9. `tar -xvf` — Extract TAR Archive

```bash
tar -xvf backup.tar
```

Extracts the contents of a TAR archive.

View contents without extracting:

```bash
tar -tvf backup.tar
```

---

### 🗜️ 10. `gzip` — Compress File

```bash
gzip report.txt
```

Creates:

```text
report.txt.gz
```

---

### 📤 11. `gunzip` — Decompress GZIP

```bash
gunzip report.txt.gz
```

Restores:

```text
report.txt
```

---

### 📦 12. `zip` — Create ZIP Archive

```bash
zip backup.zip file1.txt file2.txt
```

For a complete directory:

```bash
zip -r backup.zip my_folder/
```

> 💡 `-r` means recursive.

---

### 📂 13. `unzip` — Extract ZIP Archive

```bash
unzip backup.zip
```

Extract to another directory:

```bash
unzip backup.zip -d extracted/
```

View contents:

```bash
unzip -l backup.zip
```

---

## 🗜️ TAR + GZIP

Create a compressed TAR archive:

```bash
tar -czvf backup.tar.gz my_folder/
```

Extract it:

```bash
tar -xzvf backup.tar.gz
```

Options:

```text
-c → Create
-x → Extract
-z → GZIP
-v → Verbose
-f → Filename
```

---

## 🧪 Mini Practice

```bash
mkdir linux-practice
cd linux-practice

touch file1.txt file2.txt

tar -cvf backup.tar file1.txt file2.txt
tar -xvf backup.tar

gzip file1.txt
gunzip file1.txt.gz

zip backup.zip file1.txt file2.txt
unzip backup.zip
```

---

## 📌 Quick Revision

```text
apt update       → Update package information
apt upgrade      → Upgrade packages
apt install      → Install software
apt remove       → Remove software
apt purge        → Remove software + configuration
apt search       → Search packages
dpkg -l          → List installed packages

tar -cvf         → Create TAR
tar -xvf         → Extract TAR
tar -tvf         → View TAR contents
gzip             → Compress
gunzip           → Decompress
zip              → Create ZIP
unzip            → Extract ZIP
```

---

## 🛡️ Safety Tips

- Use `sudo` only when required.
- Run `apt update` before upgrading.
- Review packages before installing or removing.
- Be careful with `apt purge`.
- Check archive contents before extraction.
- Avoid extracting untrusted archives.
- Practice inside a separate directory.

---

## 🎯 Common Use Cases

| Task | Command |
|---|---|
| Update packages | `sudo apt update` |
| Upgrade system | `sudo apt upgrade` |
| Install software | `sudo apt install package` |
| Remove software | `sudo apt remove package` |
| Search software | `apt search keyword` |
| Create backup | `tar -czvf backup.tar.gz folder/` |
| Extract backup | `tar -xzvf backup.tar.gz` |
| Create ZIP | `zip -r backup.zip folder/` |
| Extract ZIP | `unzip backup.zip` |

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)
- [Debian Documentation](https://www.debian.org/doc/)
- [GNU Tar](https://www.gnu.org/software/tar/manual/)
- [GNU Gzip](https://www.gnu.org/software/gzip/manual/)

---

⭐ If this guide helped you learn Linux commands, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️