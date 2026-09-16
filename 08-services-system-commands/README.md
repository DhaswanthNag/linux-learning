# 🔹 Services & System Commands

Practical Linux command notes with screenshots. Replace the placeholder images in the `images/` folder with your own terminal screenshots.

## `systemctl status nginx`

Check the status of a service.

```bash
systemctl status nginx
```

![systemctl-status screenshot](images/systemctl-status.png)

## `sudo systemctl start nginx`

Start a service.

```bash
sudo systemctl start nginx
```

![systemctl-start screenshot](images/systemctl-start.png)

## `sudo systemctl stop nginx`

Stop a service.

```bash
sudo systemctl stop nginx
```

![systemctl-stop screenshot](images/systemctl-stop.png)

## `sudo systemctl restart nginx`

Restart a service.

```bash
sudo systemctl restart nginx
```

![systemctl-restart screenshot](images/systemctl-restart.png)

## `sudo systemctl enable nginx`

Enable a service at boot.

```bash
sudo systemctl enable nginx
```

![systemctl-enable screenshot](images/systemctl-enable.png)

## `sudo systemctl disable nginx`

Disable a service at boot.

```bash
sudo systemctl disable nginx
```

![systemctl-disable screenshot](images/systemctl-disable.png)

## `journalctl`

View systemd journal logs.

```bash
journalctl
```

![journalctl screenshot](images/journalctl.png)

## `journalctl -u nginx`

View logs for a specific service.

```bash
journalctl -u nginx
```

![journalctl-service screenshot](images/journalctl-service.png)

## `dmesg`

View kernel messages.

```bash
dmesg
```

![dmesg screenshot](images/dmesg.png)

## `systemctl list-units`

List active systemd units.

```bash
systemctl list-units
```

![systemctl-list screenshot](images/systemctl-list.png)

## `sudo reboot`

Restart the system.

```bash
sudo reboot
```

![reboot screenshot](images/reboot.png)

## `sudo shutdown now`

Shut down the system.

```bash
sudo shutdown now
```

![shutdown screenshot](images/shutdown.png)
