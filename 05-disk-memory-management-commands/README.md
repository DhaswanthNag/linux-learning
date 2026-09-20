# 💾 Linux Disk, Storage & Memory Commands

> A beginner-friendly reference for checking disk space, storage devices, partitions, filesystems, memory, and swap usage in Linux.

---

## 📋 Disk & Storage Commands

| Command | Purpose | Example |
|---|---|---|
| `df -h` | Shows disk space usage in human-readable format | `df -h` |
| `du -sh` | Shows directory size | `du -sh /home/user` |
| `lsblk` | Lists disks and partitions | `lsblk` |
| `lsblk -f` | Shows disks with filesystem information | `lsblk -f` |
| `blkid` | Shows UUID and filesystem information | `blkid` |
| `mount` | Mounts a filesystem/device | `sudo mount /dev/sdc1 /mnt` |
| `umount` | Unmounts a filesystem | `sudo umount /mnt` |
| `fdisk -l` | Lists disk partitions | `sudo fdisk -l` |
| `parted -l` | Shows partition information | `sudo parted -l` |

---

## 💽 1. `df -h` — Disk Space Usage

Shows available and used disk space.

```bash
df -h
```

`-h` displays sizes in a human-readable format such as GB and MB.

---

## 📁 2. `du -sh` — Directory Size

Shows the total size of a directory.

```bash
du -sh /home/user
```

- `-s` → Summary
- `-h` → Human-readable

---

## 💿 3. `lsblk` — List Block Devices

Displays disks, partitions, and mount points.

```bash
lsblk
```

---

## 🗂️ 4. `lsblk -f` — Filesystem Information

Shows filesystem type, UUID, and mount points.

```bash
lsblk -f
```

---

## 🆔 5. `blkid` — Device Information

Displays UUID and filesystem information.

```bash
sudo blkid
```

---

## 📌 6. `mount` — Mount a Filesystem

Mounts a device to a directory.

```bash
sudo mount /dev/sdc1 /mnt
```

---

## 📤 7. `umount` — Unmount a Filesystem

Unmounts a mounted filesystem.

```bash
sudo umount /mnt
```

> ⚠️ Make sure files are not being used before unmounting.

---

## 💿 8. `fdisk -l` — List Partitions

Displays partition information for disks.

```bash
sudo fdisk -l
```

> ⚠️ Be careful when using disk partitioning tools.

---

## 🧰 9. `parted -l` — Partition Information

Lists disk partitions using `parted`.

```bash
sudo parted -l
```

---

# 🧠 Memory & System Usage

| Command | Purpose | Example |
|---|---|---|
| `free -h` | Shows RAM and swap usage | `free -h` |
| `vmstat` | Reports memory and system statistics | `vmstat 1 5` |
| `sar -r 15` | Monitors memory usage | `sar -r 15` |
| `swapon --show` | Shows active swap areas | `swapon --show` |
| `cat /proc/meminfo` | Shows detailed memory information | `cat /proc/meminfo` |

---

## 🧠 10. `free -h` — Memory Usage

Displays RAM and swap usage.

```bash
free -h
```

Example information:

```text
              total   used   free
Mem:           8Gi    3Gi    2Gi
Swap:          2Gi    0Gi    2Gi
```

---

## 📊 11. `vmstat` — System Statistics

Displays memory, CPU, processes, and system statistics.

```bash
vmstat
```

Monitor continuously:

```bash
vmstat 1 5
```

This updates every second for 5 times.

---

## 📈 12. `sar -r` — Memory Monitoring

Shows memory utilization statistics.

```bash
sar -r 15
```

The command can be used to observe memory usage over time.

> ℹ️ `sar` may require the `sysstat` package.

---

## 🔄 13. `swapon --show` — Show Swap

Displays currently active swap areas.

```bash
swapon --show
```

---

## 📋 14. `/proc/meminfo` — Detailed Memory Information

Linux provides detailed memory information through `/proc/meminfo`.

```bash
cat /proc/meminfo
```

It includes information about:

- Total memory
- Free memory
- Available memory
- Cached memory
- Swap memory

---

## 🧪 Mini Practice

```bash
df -h

du -sh ~

lsblk

lsblk -f

free -h

swapon --show

cat /proc/meminfo
```

---

## 🛡️ Safety Tips

- Use `df -h` to check available disk space.
- Use `lsblk` before working with disks.
- Be careful with `mount` and `umount`.
- Never modify partitions unless you understand the command.
- Double-check the device name before using `fdisk` or `parted`.
- Use `free -h` to quickly check RAM and swap usage.

---

## 📌 Quick Revision

```text
df -h          → Disk space
du -sh         → Directory size
lsblk          → List disks
lsblk -f       → Filesystem information
blkid          → UUID / filesystem info
mount          → Mount filesystem
umount         → Unmount filesystem
fdisk -l       → List partitions
parted -l      → Partition information

free -h        → RAM / Swap usage
vmstat         → System statistics
sar -r 15      → Memory monitoring
swapon --show  → Active swap
/proc/meminfo  → Detailed memory information
```

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Coreutils](https://www.gnu.org/software/coreutils/manual/coreutils.html)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️