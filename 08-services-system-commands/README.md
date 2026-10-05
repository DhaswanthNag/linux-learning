# ⚙️ Linux System & Service Management Commands

> A beginner-friendly reference for managing Linux services, checking system information, viewing system logs, monitoring system uptime, and controlling system power.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `systemctl start` | Starts a service | `sudo systemctl start nginx` |
| `systemctl stop` | Stops a running service | `sudo systemctl stop nginx` |
| `systemctl restart` | Restarts a service | `sudo systemctl restart nginx` |
| `systemctl enable` | Enables a service at boot | `sudo systemctl enable nginx` |
| `systemctl disable` | Disables a service at boot | `sudo systemctl disable nginx` |
| `systemctl status` | Checks service status | `systemctl status nginx` |
| `journalctl` | Displays system logs | `journalctl` |
| `reboot` | Restarts the system | `sudo reboot` |
| `shutdown -h now` | Shuts down the system | `sudo shutdown -h now` |
| `uptime` | Shows system running time | `uptime` |
| `hostnamectl` | Shows system information | `hostnamectl` |

---

## ⚙️ 1. `systemctl start` — Start a Service

The `systemctl start` command starts a service immediately.

```bash
sudo systemctl start nginx
```

For example, if the Nginx web server is installed but stopped, this command starts it.

Check whether it started successfully:

```bash
systemctl status nginx
```

> 💡 Starting a service does not automatically make it start after the next reboot.

---

## 🛑 2. `systemctl stop` — Stop a Service

The `systemctl stop` command stops a currently running service.

```bash
sudo systemctl stop nginx
```

This is useful when you temporarily want to stop a service without uninstalling it.

Check the status:

```bash
systemctl status nginx
```

> ⚠️ Stopping an important system service may affect applications that depend on it.

---

## 🔄 3. `systemctl restart` — Restart a Service

The `systemctl restart` command stops and starts a service again.

```bash
sudo systemctl restart nginx
```

It is commonly used after changing a service's configuration.

Example:

```bash
sudo systemctl restart nginx
```

Then verify:

```bash
systemctl status nginx
```

> 💡 Restarting is useful when a service needs to reload its configuration or recover from an issue.

---

## 🟢 4. `systemctl enable` — Start Service at Boot

The `systemctl enable` command configures a service to start automatically when Linux boots.

```bash
sudo systemctl enable nginx
```

Check whether it is enabled:

```bash
systemctl is-enabled nginx
```

> ℹ️ `enable` controls future boots. It does not necessarily start the service immediately.

To enable and start it immediately:

```bash
sudo systemctl enable --now nginx
```

---

## 🔴 5. `systemctl disable` — Disable Service at Boot

The `systemctl disable` command prevents a service from starting automatically during system boot.

```bash
sudo systemctl disable nginx
```

Check the setting:

```bash
systemctl is-enabled nginx
```

> 💡 Disabling a service does not necessarily stop it if it is currently running.

To stop it and disable it:

```bash
sudo systemctl disable --now nginx
```

---

## ℹ️ 6. `systemctl status` — Check Service Status

The `systemctl status` command provides information about a service.

```bash
systemctl status nginx
```

It can show:

- Whether the service is running
- Whether it is enabled
- When it was started
- Recent log messages
- The service process ID

Common statuses include:

```text
active (running)
inactive (dead)
failed
```

> 💡 This is one of the first commands to use when troubleshooting a service.

---

## 📜 7. `journalctl` — View System Logs

The `journalctl` command displays logs collected by the systemd journal.

View all available logs:

```bash
journalctl
```

View the latest 50 entries:

```bash
journalctl -n 50
```

View logs for a specific service:

```bash
journalctl -u nginx
```

View recent service logs:

```bash
journalctl -u nginx -n 50
```

Follow new logs as they appear:

```bash
journalctl -u nginx -f
```

> 💡 Logs are extremely useful for finding errors when a service fails to start.

---

## 🔁 8. `reboot` — Restart the System

The `reboot` command restarts the Linux system.

```bash
sudo reboot
```

The system will close running processes and restart.

> ⚠️ Save your files and close important applications before rebooting.

---

## 📴 9. `shutdown -h now` — Shut Down the System

This command shuts down the system immediately.

```bash
sudo shutdown -h now
```

The `-h` option tells the system to halt/power off.

> ⚠️ Save your work before shutting down the system.

You can also schedule a shutdown:

```bash
sudo shutdown -h +10
```

This schedules the shutdown for 10 minutes later.

---

## ⏱️ 10. `uptime` — Check System Running Time

The `uptime` command shows how long the system has been running.

```bash
uptime
```

Example:

```text
22:30:10 up 2 days, 4:15, 1 user, load average: 0.10, 0.15, 0.20
```

It provides:

- Current time
- System uptime
- Number of logged-in users
- System load averages

> 💡 Useful for quickly checking whether a system has been running continuously.

---

## 🖥️ 11. `hostnamectl` — System Information

The `hostnamectl` command displays information about the system hostname and operating system.

```bash
hostnamectl
```

It can show information such as:

- Hostname
- Operating system
- Kernel
- Architecture

Change the hostname:

```bash
sudo hostnamectl set-hostname new-name
```

Check the new hostname:

```bash
hostnamectl
```

> ⚠️ Only change the hostname if you understand how it may affect your system or network configuration.

---

## 🧪 Mini Practice

Check your system information:

```bash
hostnamectl
```

Check how long the system has been running:

```bash
uptime
```

Check a service:

```bash
systemctl status nginx
```

Check whether it starts at boot:

```bash
systemctl is-enabled nginx
```

View its logs:

```bash
journalctl -u nginx -n 20
```

> 💡 The Nginx examples require Nginx to be installed. You can replace `nginx` with another installed service.

---

## 🔄 Common Service Workflow

A common workflow when working with a service is:

```bash
# Check the service
systemctl status nginx

# Start it
sudo systemctl start nginx

# Check again
systemctl status nginx

# Enable it at boot
sudo systemctl enable nginx

# Restart after configuration changes
sudo systemctl restart nginx

# Check logs if something goes wrong
journalctl -u nginx
```

---

## 🛡️ Safety Tips

- Use `sudo` only when administrative privileges are required.
- Check service status before stopping or restarting services.
- Do not stop important system services without understanding their purpose.
- Save your work before using `reboot` or `shutdown`.
- Use `journalctl` to investigate service failures.
- Be careful when changing the hostname.
- Avoid disabling system services unless you know why they are running.
- Double-check commands before executing them on a production system.

---

## 📌 Quick Revision

```text
systemctl start       → Start a service
systemctl stop        → Stop a service
systemctl restart     → Restart a service
systemctl enable      → Enable service at boot
systemctl disable     → Disable service at boot
systemctl status      → Check service status
journalctl            → View system logs
reboot                → Restart the system
shutdown -h now       → Shut down the system
uptime                → Show system running time
hostnamectl           → Show system information
```

---

## 🎯 When to Use These Commands

| Situation | Command |
|---|---|
| Start a service | `sudo systemctl start service` |
| Stop a service | `sudo systemctl stop service` |
| Restart after configuration changes | `sudo systemctl restart service` |
| Start service automatically at boot | `sudo systemctl enable service` |
| Prevent service from starting at boot | `sudo systemctl disable service` |
| Check why a service is not working | `systemctl status service` |
| Check service logs | `journalctl -u service` |
| Check system uptime | `uptime` |
| Check system information | `hostnamectl` |
| Restart the computer | `sudo reboot` |
| Shut down the computer | `sudo shutdown -h now` |

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [systemd Documentation](https://systemd.io/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)

---

⭐ If this guide helped you learn Linux commands, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️