# 🔐 Linux Permissions & Ownership Commands
> A beginner-friendly reference for managing file permissions, ownership, groups, and access control in Linux.
---
## 📋 Commands at a Glance
| Command | Purpose | Example |
|---|---|---|
| `ls -l` | View permissions and ownership | `ls -l` |
| `ls -la` | View hidden files with permissions | `ls -la` |
| `stat` | View detailed file information | `stat file.txt` |
| `chmod` | Change permissions | `chmod 755 file.sh` |
| `chmod +x` | Make a file executable | `chmod +x script.sh` |
| `chown` | Change file owner | `sudo chown user file.txt` |
| `chgrp` | Change group owner | `sudo chgrp devs file.txt` |
| `groups` | View a user's groups | `groups username` |
| `id` | View user and group IDs | `id username` |
| `umask` | View default permission mask | `umask` |
| `getfacl` | View ACL permissions | `getfacl file.txt` |
| `setfacl` | Set ACL permissions | `setfacl -m u:alice:r file.txt` |
| `chown -R` | Change ownership recursively | `sudo chown -R user mydir/` |
| `chmod -R` | Change permissions recursively | `chmod -R 755 mydir/` |
---
## 📚 Table of Contents
1. [`ls -l` — View Permissions](#-1-ls--l--view-permissions)
2. [Permission Structure](#permission-structure)
3. [`chmod` — Change Permissions](#-2-chmod--change-permissions)
4. [Numeric Permission Values](#numeric-permission-values)
5. [Symbolic Permissions](#symbolic-permissions)
6. [`chmod +x` — Make Executable](#️-3-chmod-x--make-executable)
7. [`chown` — Change Owner](#-4-chown--change-owner)
8. [`chgrp` — Change Group](#-5-chgrp--change-group)
9. [`chown -R` — Change Ownership Recursively](#-6-chown--r--change-ownership-recursively)
10. [`chmod -R` — Change Permissions Recursively](#-7-chmod--r--change-permissions-recursively)
11. [Files and Directories](#files-and-directories)
12. [Special Permissions](#special-permissions)
13. [`umask` — Default Permissions](#-umask--default-permissions)
14. [Groups and Group Membership](#groups-and-group-membership)
15. [ACL Permissions](#acl-permissions)
16. [Checking and Troubleshooting Permissions](#checking-and-troubleshooting-permissions)
17. [Mini Practice](#-mini-practice)
18. [Safety Tips](#️-safety-tips)
19. [Quick Revision](#-quick-revision)
---
## 🔎 1. `ls -l` — View Permissions
```bash
ls -l
```
Example:
```text
-rwxr-xr-- 1 user user 1024 Sep 25 10:30 file.txt
```
The output contains:
```text
-rwxr-xr-- 1 user user 1024 Sep 25 10:30 file.txt
│├──┼──┼──┘ │    │    │     │          └── File name
││  │  │    │    │    │     └──────────── Modification date and time
││  │  │    │    │    └────────────────── File size
││  │  │    │    └─────────────────────── Group owner
││  │  │    └──────────────────────────── User owner
││  │  └───────────────────────────────── Others permissions
││  └──────────────────────────────────── Group permissions
│└─────────────────────────────────────── Owner permissions
└──────────────────────────────────────── File type
```
### File Type Characters
| Character | Meaning |
|---|---|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |
| `c` | Character device |
| `b` | Block device |
| `s` | Socket |
| `p` | Named pipe |
### Permission Characters
- `r` → Read
- `w` → Write
- `x` → Execute
- `-` → No permission
---
## 🔐 Permission Structure
```text
-rwxr-xr--
 │   │  │
 │   │  └── Others
 │   └───── Group
 └──────── Owner
```
The permissions are divided into three categories:
| Category | Symbol | Applies To |
|---|---|---|
| User | `u` | File owner |
| Group | `g` | Users in the assigned group |
| Others | `o` | Everyone else |
| All | `a` | User, group, and others |
---
## 🔑 2. `chmod` — Change Permissions
`chmod` means **change mode**. It changes the read, write, and execute permissions of a file or directory.
```bash
chmod 755 file.sh
```
General syntax:
```bash
chmod [options] permissions file
```
Examples:
```bash
chmod 644 document.txt
chmod 755 script.sh
chmod 700 private-folder
chmod u+x backup.sh
```
---
## 🔢 Numeric Permission Values
Each permission has a numeric value:
| Number | Meaning |
|---|---|
| `0` | No permission |
| `1` | Execute |
| `2` | Write |
| `3` | Write + Execute |
| `4` | Read |
| `5` | Read + Execute |
| `6` | Read + Write |
| `7` | Read + Write + Execute |
```
Read    = 4
Write   = 2
Execute = 1
```
### How Numeric Permissions Work
```bash
chmod 754 file.txt
```
The three digits represent:
```text
7   5   4
│   │   └── Others: Read
│   └────── Group: Read + Execute
└────────── Owner: Read + Write + Execute
```
### Common Permission Combinations
| Numeric | Symbolic | Typical Use |
|---|---|---|
| `600` | `rw-------` | Private file |
| `644` | `rw-r--r--` | Normal text or configuration file |
| `660` | `rw-rw----` | Shared group file |
| `700` | `rwx------` | Private directory or script |
| `755` | `rwxr-xr-x` | Public executable or directory |
| `750` | `rwxr-x---` | Group-accessible directory |
| `775` | `rwxrwxr-x` | Shared development directory |
| `777` | `rwxrwxrwx` | Full access for everyone; generally unsafe |
---
## ✏️ Symbolic Permissions
Symbolic mode uses letters instead of numbers:
```bash
chmod u+x script.sh
```
### Operators
| Operator | Meaning |
|---|---|
| `+` | Add permission |
| `-` | Remove permission |
| `=` | Set exact permission |
### Examples
```bash
chmod u+x script.sh
chmod u-x script.sh
chmod g+w shared.txt
chmod g-w shared.txt
chmod o-r secret.txt
chmod a+r public.txt
chmod u=rw,g=r,o= file.txt
```
### Multiple Changes
```bash
chmod u+x,g+rw,o-rwx project.sh
```
This means:
- Add execute permission for the owner.
- Add read and write permissions for the group.
- Remove all permissions from others.
### Copy Permissions
```bash
chmod g=u file.txt
```
This gives the group the same permissions as the owner.
```bash
chmod o=g file.txt
```
This gives others the same permissions as the group.
---
## ▶️ 3. `chmod +x` — Make Executable
```bash
chmod +x script.sh
```
Run the script:
```bash
./script.sh
```
A shell script normally starts with a shebang:
```bash
#!/bin/bash
echo "Hello from Linux"
```
You can also run a script through the shell without execute permission:
```bash
bash script.sh
```
Remove execute permission:
```bash
chmod -x script.sh
```
Check the result:
```bash
ls -l script.sh
```
Expected output may look like:
```text
-rwxr-xr-x 1 user user 120 Sep 25 10:30 script.sh
```
---
## 👤 4. `chown` — Change Owner
`chown` changes the owner of a file or directory.
```bash
sudo chown newuser file.txt
```
Change owner and group:
```bash
sudo chown newuser:devs file.txt
```
Change only the group:
```bash
sudo chown :devs file.txt
```
Change ownership of several files:
```bash
sudo chown newuser file1.txt file2.txt file3.txt
```
Verify ownership:
```bash
ls -l file.txt
```
### Important Notes
- Only the file owner or `root` can usually change ownership.
- Changing ownership often requires `sudo`.
- Confirm the username and path before running the command.
---
## 👥 5. `chgrp` — Change Group
`chgrp` changes the group owner of a file or directory.
```bash
sudo chgrp devs file.txt
```
Change the group for multiple files:
```bash
sudo chgrp devs file1.txt file2.txt
```
Change the group recursively:
```bash
sudo chgrp -R devs project/
```
Check the group:
```bash
ls -l file.txt
```
---
## 🔄 6. `chown -R` — Change Ownership Recursively
```bash
sudo chown -R newuser mydir/
```
Change both user and group recursively:
```bash
sudo chown -R newuser:devs mydir/
```
> ⚠️ `-R` affects the directory and everything inside it.
> Always verify the path before using a recursive ownership command.
A safer approach is to inspect the directory first:
```bash
find mydir/ -maxdepth 2 -print
```
---
## 🔁 7. `chmod -R` — Change Permissions Recursively
```bash
chmod -R 755 mydir/
```
> ⚠️ Be careful when changing permissions recursively.
Using `755` for every item may give execute permission to regular files. A safer approach is to use different permissions for directories and files:
```bash
find mydir/ -type d -exec chmod 755 {} \;
find mydir/ -type f -exec chmod 644 {} \;
```
For private content:
```bash
find private-data/ -type d -exec chmod 700 {} \;
find private-data/ -type f -exec chmod 600 {} \;
```
---
## 📁 Files and Directories
Permissions behave differently for files and directories.
### Regular Files
| Permission | Meaning |
|---|---|
| Read `r` | View file contents |
| Write `w` | Modify file contents |
| Execute `x` | Run the file as a program or script |
### Directories
| Permission | Meaning |
|---|---|
| Read `r` | List directory contents |
| Write `w` | Create, delete, or rename entries |
| Execute `x` | Enter the directory and access known files |
### Directory Examples
```bash
chmod 755 public/
chmod 700 private/
chmod 770 shared/
```
A directory usually needs execute permission to be accessed:
```bash
cd project/
```
Even if a directory has read permission, users may not be able to enter it without execute permission.
---
## ⭐ Special Permissions
Linux supports special permission bits for specific use cases.
### Setuid
Setuid allows an executable to run with the permissions of its owner.
```bash
chmod u+s program
```
Numeric form:
```bash
chmod 4755 program
```
View setuid:
```bash
ls -l program
```
Example:
```text
-rwsr-xr-x
```
> ⚠️ Setuid can create security risks. Use it only when required.
### Setgid
Setgid on a file runs it with the file's group permissions. On a directory, newly created files inherit the directory's group.
```bash
chmod g+s shared/
```
Numeric form:
```bash
chmod 2775 shared/
```
Example:
```text
drwxrwsr-x
```
### Sticky Bit
The sticky bit on a directory allows users to delete only files they own.
```bash
chmod +t shared/
```
Numeric form:
```bash
chmod 1777 shared/
```
Example:
```text
drwxrwxrwt
```
The `/tmp` directory commonly uses the sticky bit.
### Special Permission Summary
| Permission | Numeric Value | Purpose |
|---|---:|---|
| Setuid | `4000` | Run with owner's permissions |
| Setgid | `2000` | Run with group's permissions or inherit directory group |
| Sticky bit | `1000` | Restrict deletion in shared directories |
---
## 🧮 `umask` — Default Permissions
`umask` controls which permissions are removed when new files and directories are created.
View the current umask:
```bash
umask
```
Display it symbolically:
```bash
umask -S
```
Example:
```text
0022
```
A common result is:
- New files: `644`
- New directories: `755`
Test the current default permissions:
```bash
touch test-file.txt
mkdir test-directory
ls -ld test-file.txt test-directory
```
Set a temporary umask for the current shell:
```bash
umask 027
```
> The exact permissions also depend on the program creating the file. New files normally do not receive execute permission automatically.
---
## 👨‍👩‍👧 Groups and Group Membership
View the current user's groups:
```bash
groups
```
View another user's groups:
```bash
groups username
```
View detailed user and group IDs:
```bash
id
id username
```
Add a user to a group:
```bash
sudo usermod -aG devs username
```
> Use `-aG` together. Omitting `-a` can replace the user's existing supplementary groups.
Apply the new group membership by logging out and logging in again, or run:
```bash
newgrp devs
```
Create a group:
```bash
sudo groupadd devs
```
Remove a user from a group:
```bash
sudo gpasswd -d username devs
```
---
## 🧾 `stat` — View Detailed File Information
```bash
stat file.txt
```
Example information includes:
- File size
- File type
- Owner and group IDs
- Access permissions
- Access time
- Modification time
- Metadata change time
Useful format:
```bash
stat -c "%A %a %U %G %n" file.txt
```
Output may look like:
```text
-rw-r--r-- 644 user user file.txt
```
---
## 🔐 ACL Permissions
Access Control Lists allow permissions for specific users or groups beyond the normal owner/group/others model.
Check ACL support and current permissions:
```bash
getfacl file.txt
```
Give a user read permission:
```bash
setfacl -m u:alice:r file.txt
```
Give a user read and write permission:
```bash
setfacl -m u:alice:rw file.txt
```
Give a group read and execute permission on a directory:
```bash
setfacl -m g:developers:rx project/
```
Remove a user's ACL entry:
```bash
setfacl -x u:alice file.txt
```
Remove all extended ACL entries:
```bash
setfacl -b file.txt
```
Set a default ACL for new files inside a directory:
```bash
setfacl -m d:g:developers:rwx project/
```
> ACL commands may require the `acl` package to be installed on some Linux distributions.
---
## 🔍 Checking and Troubleshooting Permissions
### Check a File
```bash
ls -l file.txt
stat file.txt
```
### Check Every Directory in a Path
```bash
namei -l /path/to/file.txt
```
### Find Files with Specific Permissions
Find world-writable files:
```bash
find . -type f -perm -002 -print
```
Find files with exactly `644` permissions:
```bash
find . -type f -perm 644 -print
```
Find directories without owner execute permission:
```bash
find . -type d ! -perm -u=x -print
```
### Find Files Owned by a User
```bash
find /var/www -user username -print
```
### Find Files Owned by a Group
```bash
find /var/www -group devs -print
```
### Common Error: Permission Denied
If you see:
```text
Permission denied
```
Check:
1. The file or directory path.
2. The permissions using `ls -l`.
3. The owner and group.
4. Execute permission on every parent directory.
5. Whether the operation requires `sudo`.
6. Whether an ACL is overriding the expected access.
Use:
```bash
namei -l /path/to/file
```
### Common Error: Operation Not Permitted
This may happen when:
- You are not the owner.
- The file belongs to another user.
- The filesystem is mounted read-only.
- The file has an immutable attribute.
Check file attributes:
```bash
lsattr file.txt
```
Remove the immutable attribute if appropriate:
```bash
sudo chattr -i file.txt
```
> ⚠️ Do not remove special attributes unless you understand why they were set.
---
## 🧪 Mini Practice
```bash
mkdir permissions-practice
cd permissions-practice
touch file.txt
mkdir private-folder
printf '#!/bin/bash\necho "Practice script"\n' > script.sh
ls -la
chmod 644 file.txt
chmod 700 private-folder
chmod +x script.sh
ls -la
./script.sh
stat file.txt
cd ..
```
Expected permission examples:
```text
file.txt       → -rw-r--r--
private-folder → drwx------
script.sh      → -rwxr-xr-x
```
Clean up the practice directory:
```bash
rm -rf permissions-practice
```
> Only run the cleanup command when you are certain that the directory contains practice files.
---
## 🛡️ Safety Tips
- Always check permissions with `ls -l`.
- Use `stat` when you need detailed metadata.
- Be careful with `sudo`.
- Double-check paths before using `chown -R` or `chmod -R`.
- Avoid unnecessary `777` permissions.
- Do not use `chmod -R 777` on system directories.
- Prefer the minimum permissions required.
- Use `find` to apply different permissions to files and directories.
- Practice in a test directory first.
- Avoid changing ownership of system files unless you know the consequences.
- Be careful when running commands as `root`.
- Use ACLs when only a particular user or group needs additional access.
- Remember that permission changes may affect applications, services, and other users.
---
## 📌 Quick Revision
```text
ls -l       → View permissions and ownership
ls -la      → View hidden files and permissions
stat        → View detailed file information
chmod       → Change permissions
chmod +x    → Make executable
chown       → Change owner
chgrp       → Change group
groups      → View group membership
id          → View user and group IDs
umask       → View default permission restrictions
getfacl     → View ACL permissions
setfacl     → Set ACL permissions
chown -R    → Change owner recursively
chmod -R    → Change permissions recursively
```
---
## 📊 Common Permission Examples
| Situation | Recommended Command |
|---|---|
| Private file | `chmod 600 file.txt` |
| Normal text file | `chmod 644 file.txt` |
| Private script | `chmod 700 script.sh` |
| Public script | `chmod 755 script.sh` |
| Private directory | `chmod 700 private/` |
| Shared group directory | `chmod 2770 shared/` |
| Public read-only directory | `chmod 755 public/` |
| Add execute permission to owner | `chmod u+x script.sh` |
| Remove write permission from others | `chmod o-w file.txt` |
---
## 🧠 Important Concepts
### Permission Changes Are Not the Same as Ownership Changes
```bash
chmod 644 file.txt
```
Changes permissions.
```bash
sudo chown alice:developers file.txt
```
Changes ownership.
### `sudo` Does Not Permanently Change Your User
Running a command with `sudo` temporarily executes that command with elevated privileges. It does not change your login user or permanently grant ownership.
### Root Can Override Most Permissions
The `root` user can normally access files regardless of standard permission bits. However, special filesystem restrictions, read-only mounts, ACLs, and security systems such as SELinux or AppArmor may still affect access.
### Permissions Are Only One Layer of Linux Security
Other security layers may include:
- File ownership
- ACLs
- SELinux
- AppArmor
- Filesystem mount options
- User and group membership
- Process permissions
---
## 📚 References
- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html )
- [Linux man-pages](https://man7.org/linux/man-pages/ )
- [GNU Bash Reference](https://www.gnu.org/software/bash/manual/bash.html )
- [chmod Manual](https://man7.org/linux/man-pages/man1/chmod.1.html )
- [chown Manual](https://man7.org/linux/man-pages/man1/chown.1.html )
- [ls Manual](https://man7.org/linux/man-pages/man1/ls.1.html )
- [find Manual](https://man7.org/linux/man-pages/man1/find.1.html )
- [ACL Manual](https://man7.org/linux/man-pages/man5/acl.5.html )
---
⭐ If this guide helped you learn Linux, consider starring the repository!
Made for Linux beginners with 🐧 and ❤️
