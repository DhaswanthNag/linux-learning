# ⚙️ Linux System & Service Management Commands

> A beginner-friendly reference for managing services, checking system information, viewing logs, and controlling system power.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `systemctl start` | Start a service | `sudo systemctl start nginx` |
| `systemctl stop` | Stop a service | `sudo systemctl stop nginx` |
| `systemctl restart` | Restart a service | `sudo systemctl restart nginx` |
| `systemctl enable` | Start service at boot | `sudo systemctl enable nginx` |
| `systemctl disable` | Disable service at boot | `sudo systemctl disable nginx` |
| `systemctl status` | Check service status | `systemctl status nginx` |
| `journalctl` | View system logs | `journalctl` |
| `reboot` | Restart the system | `sudo reboot` |
| `shutdown -h now` | Shut down the system | `sudo shutdown -h now` |
| `uptime` | Show system running time | `uptime` |
| `hostnamectl` | Show system hostname/info | `hostnamectl` |

---

## ⚙️ 1. `systemctl start` — Start a Service

```bash
sudo systemctl start nginx
```

Starts the specified service.

---

## 🛑 2. `systemctl stop` — Stop a Service

```bash
sudo systemctl stop nginx
```

Stops a running service.

---

## 🔄 3. `systemctl restart` — Restart a Service

```bash
sudo systemctl restart nginx
```

Stops and starts the service again.

---

## 🟢 4. `systemctl enable` — Enable at Boot

```bash
sudo systemctl enable nginx
```

Configures the service to start automatically when the system boots.

---

## 🔴 5. `systemctl disable` — Disable at Boot

```bash
sudo systemctl disable nginx
```

Prevents the service from starting automatically at boot.

---

## ℹ️ 6. `systemctl status` — Check Service Status

```bash
systemctl status nginx
```

Shows whether the service is running, stopped, or failed.

---

## 📜 7. `journalctl` — View System Logs

```bash
journalctl
```

View recent logs:

```bash
journalctl -n 50
```

View logs for a service:

```bash
journalctl -u nginx
```

---

## 🔁 8. `reboot` — Restart the System

```bash
sudo reboot
```

Immediately restarts the system.

> ⚠️ Save your work before rebooting.

---

## 📴 9. `shutdown -h now` — Shut Down

```bash
sudo shutdown -h now
```

Shuts down the system immediately.

> ⚠️ Save your work before using this command.

---

## ⏱️ 10. `uptime` — System Running Time

```bash
uptime
```

Shows how long the system has been running and basic load information.

---

## 🖥️ 11. `hostnamectl` — System Information

```bash
hostnamectl
```

Displays hostname and system information.

---

## 🧪 Mini Practice

```bash
systemctl status nginx

systemctl is-enabled nginx

journalctl -u nginx

uptime

hostnamectl
```

> 💡 The `nginx` examples require Nginx to be installed.

---

## 🛡️ Safety Tips

- Use `sudo` only when required.
- Check service status before stopping a service.
- Be careful when restarting or stopping important services.
- Save your work before `reboot` or `shutdown`.
- Use `journalctl` to investigate service errors.
- Avoid disabling system services unless you understand their purpose.

---

## 📌 Quick Revision

```text
systemctl start      → Start service
systemctl stop       → Stop service
systemctl restart    → Restart service
systemctl enable     → Start service at boot
systemctl disable    → Disable service at boot
systemctl status     → Check service status
journalctl           → View system logs
reboot               → Restart system
shutdown -h now      → Shut down system
uptime               → Show running time
hostnamectl          → Show system information
```

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [systemd Documentation](https://systemd.io/)
- [Ubuntu Documentation](https://documentation.ubuntu.com/)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️