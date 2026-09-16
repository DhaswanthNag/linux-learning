# 🔹 Process Management Commands

Practical Linux command notes with screenshots. Replace the placeholder images in the `images/` folder with your own terminal screenshots.

## `ps`

Display running processes.

```bash
ps
```

![ps screenshot](images/ps.png)

## `ps aux`

Display detailed processes for all users.

```bash
ps aux
```

![ps-aux screenshot](images/ps-aux.png)

## `top`

Monitor processes interactively.

```bash
top
```

![top screenshot](images/top.png)

## `htop`

Interactive process viewer (if installed).

```bash
htop
```

![htop screenshot](images/htop.png)

## `pgrep nginx`

Find process IDs by name.

```bash
pgrep nginx
```

![pgrep screenshot](images/pgrep.png)

## `pidof ssh`

Find the PID of a program.

```bash
pidof ssh
```

![pidof screenshot](images/pidof.png)

## `kill PID`

Send a signal to a process.

```bash
kill PID
```

![kill screenshot](images/kill.png)

## `kill -9 PID`

Forcefully terminate a process.

```bash
kill -9 PID
```

![kill-9 screenshot](images/kill-9.png)

## `jobs`

Show shell background jobs.

```bash
jobs
```

![jobs screenshot](images/jobs.png)

## `bg`

Resume a suspended job in the background.

```bash
bg
```

![bg screenshot](images/bg.png)

## `fg`

Bring a background job to the foreground.

```bash
fg
```

![fg screenshot](images/fg.png)

## `nohup command &`

Run a command that can continue after logout.

```bash
nohup command &
```

![nohup screenshot](images/nohup.png)
