# 🔹 Permission & Ownership Commands

Practical Linux command notes with screenshots. Replace the placeholder images in the `images/` folder with your own terminal screenshots.

## `ls -l`

View file permissions and ownership.

```bash
ls -l
```

![ls-l screenshot](images/ls-l.png)

## `chmod 644 notes.txt`

Change file permissions.

```bash
chmod 644 notes.txt
```

![chmod screenshot](images/chmod.png)

## `chmod +x script.sh`

Make a script executable.

```bash
chmod +x script.sh
```

![chmod-executable screenshot](images/chmod-executable.png)

## `sudo chown user notes.txt`

Change file owner.

```bash
sudo chown user notes.txt
```

![chown screenshot](images/chown.png)

## `sudo chown user:group notes.txt`

Change owner and group.

```bash
sudo chown user:group notes.txt
```

![chown-group screenshot](images/chown-group.png)

## `sudo chgrp developers notes.txt`

Change group ownership.

```bash
sudo chgrp developers notes.txt
```

![chgrp screenshot](images/chgrp.png)

## `umask`

Display or change the default permission mask.

```bash
umask
```

![umask screenshot](images/umask.png)

## `stat notes.txt`

Show detailed file metadata.

```bash
stat notes.txt
```

![stat screenshot](images/stat.png)
