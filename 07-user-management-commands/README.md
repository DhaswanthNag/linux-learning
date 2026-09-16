# 🔹 User Management Commands

Practical Linux command notes with screenshots. Replace the placeholder images in the `images/` folder with your own terminal screenshots.

## `whoami`

Show the current user.

```bash
whoami
```

![whoami screenshot](images/whoami.png)

## `id`

Show user and group IDs.

```bash
id
```

![id screenshot](images/id.png)

## `who`

Show logged-in users.

```bash
who
```

![who screenshot](images/who.png)

## `w`

Show logged-in users and their activity.

```bash
w
```

![w screenshot](images/w.png)

## `groups`

Show groups for a user.

```bash
groups
```

![groups screenshot](images/groups.png)

## `passwd`

Change a user's password.

```bash
passwd
```

![passwd screenshot](images/passwd.png)

## `su username`

Switch to another user.

```bash
su username
```

![su screenshot](images/su.png)

## `sudo command`

Run a command with elevated privileges.

```bash
sudo command
```

![sudo screenshot](images/sudo.png)

## `sudo useradd username`

Create a user (administrative use).

```bash
sudo useradd username
```

![useradd screenshot](images/useradd.png)

## `sudo usermod -aG group username`

Modify a user account.

```bash
sudo usermod -aG group username
```

![usermod screenshot](images/usermod.png)

## `sudo userdel username`

Delete a user account.

```bash
sudo userdel username
```

![userdel screenshot](images/userdel.png)

## `sudo groupadd developers`

Create a group.

```bash
sudo groupadd developers
```

![groupadd screenshot](images/groupadd.png)

## `sudo groupdel developers`

Delete a group.

```bash
sudo groupdel developers
```

![groupdel screenshot](images/groupdel.png)
