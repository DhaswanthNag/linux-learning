Sure 👍 Here is the **short and clean README** for all the **User & Group Management commands** shown in the image. Copy the **whole box** into your `README.md`.

````markdown
# 👥 Linux User & Group Management Commands

> A beginner-friendly reference for creating, modifying, deleting, and managing Linux users and groups.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `useradd` | Create a new user | `sudo useradd dev` |
| `passwd` | Set/change user password | `sudo passwd dev` |
| `usermod` | Modify an existing user | `sudo usermod -aG sudo dev` |
| `userdel` | Delete a user | `sudo userdel dev` |
| `groupadd` | Create a new group | `sudo groupadd devs` |
| `groupdel` | Delete a group | `sudo groupdel devs` |
| `id` | Show user and group IDs | `id user` |
| `groups` | Show user's groups | `groups user` |
| `su` | Switch to another user | `su - user` |
| `sudo` | Run command as another user/root | `sudo command` |

---

## 👤 1. `useradd` — Create User

Creates a new Linux user.

```bash
sudo useradd dev
```

Create a user with a home directory:

```bash
sudo useradd -m dev
```

---

## 🔑 2. `passwd` — Set Password

Sets or changes a user's password.

```bash
sudo passwd dev
```

Follow the prompts to enter the new password.

---

## ⚙️ 3. `usermod` — Modify User

Modifies an existing user account.

Add user to a group:

```bash
sudo usermod -aG sudo dev
```

Check the user:

```bash
id dev
```

> ⚠️ Use `-aG` when adding a user to a supplementary group so existing group memberships are preserved.

---

## 🗑️ 4. `userdel` — Delete User

Deletes a user account.

```bash
sudo userdel dev
```

Delete the user and their home directory:

```bash
sudo userdel -r dev
```

> ⚠️ Be careful with `-r` because it removes the user's home directory and its contents.

---

## 👥 5. `groupadd` — Create Group

Creates a new group.

```bash
sudo groupadd devs
```

Check the group:

```bash
getent group devs
```

---

## 🗑️ 6. `groupdel` — Delete Group

Deletes an existing group.

```bash
sudo groupdel devs
```

> ⚠️ Make sure the group is no longer needed before deleting it.

---

## 🆔 7. `id` — Display User Information

Shows user ID and group information.

```bash
id
```

For a specific user:

```bash
id dev
```

Example:

```text
uid=1001(dev) gid=1001(dev) groups=1001(dev)
```

---

## 👥 8. `groups` — Show User Groups

Displays the groups a user belongs to.

```bash
groups
```

For a specific user:

```bash
groups dev
```

---

## 🔄 9. `su` — Switch User

Switches to another user account.

```bash
su - dev
```

Switch to root:

```bash
su -
```

Return to the previous user:

```bash
exit
```

---

## 🔐 10. `sudo` — Run as Another User

Runs a command with elevated privileges.

```bash
sudo command
```

Example:

```bash
sudo apt update
```

Run a command as another user:

```bash
sudo -u dev command
```

> ⚠️ Use `sudo` carefully because commands run with elevated privileges can modify important system files.

---

## 🧪 Mini Practice

```bash
sudo useradd -m linuxuser

sudo passwd linuxuser

sudo groupadd practice

sudo usermod -aG practice linuxuser

id linuxuser

groups linuxuser

su - linuxuser

exit
```

---

## 🛡️ Safety Tips

- Be careful when using `sudo`.
- Double-check usernames before deleting users.
- Be careful with `userdel -r`.
- Avoid modifying system users unless you understand their purpose.
- Use `id` and `groups` to verify group membership.
- Never share user passwords.
- Use strong passwords for user accounts.

---

## 📌 Quick Revision

```text
useradd   → Create user
passwd    → Set/change password
usermod   → Modify user
userdel   → Delete user
groupadd  → Create group
groupdel  → Delete group
id        → Show user/group IDs
groups    → Show user's groups
su        → Switch user
sudo      → Run command with privileges
```

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Coreutils Manual](https://www.gnu.org/software/coreutils/manual/coreutils.html)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️
````
