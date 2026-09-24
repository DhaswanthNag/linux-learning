# Linux Service and System Commands

This README explains the Linux commands shown in the reference image. Most examples use `nginx` as the service name. Replace `nginx` with the name of the service you want to manage.

## Prerequisites

- Use `sudo` unless you are logged in as `root`.
- These commands are mainly used on Linux systems that use `systemd`.
- The service name must exist on your system.

---

## 1. systemctl start

Starts a service immediately.

Syntax:

sudo systemctl start <service-name>

Example:

sudo systemctl start nginx

This starts Nginx for the current session. It does not configure Nginx to start automatically after reboot.

---

## 2. systemctl stop

Stops a running service immediately.

Syntax:

sudo systemctl stop <service-name>

Example:

sudo systemctl stop nginx

Stopping a service may interrupt applications that depend on it.

---

## 3. systemctl restart

Stops and starts a service again.

Syntax:

sudo systemctl restart <service-name>

Example:

sudo systemctl restart nginx

This command is commonly used after changing a service configuration.

To reload the configuration without completely stopping the service:

sudo systemctl reload nginx

---

## 4. systemctl enable

Configures a service to start automatically when the system boots.

Syntax:

sudo systemctl enable <service-name>

Example:

sudo systemctl enable nginx

To enable and start a service at the same time:

sudo systemctl enable --now nginx

---

## 5. systemctl disable

Prevents a service from starting automatically during system boot.

Syntax:

sudo systemctl disable <service-name>

Example:

sudo systemctl disable nginx

To disable and stop the service immediately:

sudo systemctl disable --now nginx

---

## 6. systemctl status

Displays the current status of a service.

Syntax:

systemctl status <service-name>

Example:

systemctl status nginx

Common service states:

- active (running) - The service is running.
- inactive (dead) - The service is not running.
- failed - The service failed to start or stopped because of an error.
- enabled - The service starts automatically at boot.
- disabled - The service does not start automatically at boot.

Useful commands:

systemctl is-active nginx

systemctl is-enabled nginx

systemctl --no-pager status nginx

---

## 7. journalctl

Displays logs collected by systemd-journald.

View logs for a service:

sudo journalctl -u nginx

View the last 50 log entries:

sudo journalctl -u nginx -n 50

Follow logs in real time:

sudo journalctl -u nginx -f

Press Ctrl+C to stop following the logs.

View logs from the current boot:

sudo journalctl -b

View logs from the previous boot:

sudo journalctl -b -1

View logs from the last hour:

sudo journalctl --since "1 hour ago"

View logs without a pager:

sudo journalctl -u nginx --no-pager

---

## 8. reboot

Restarts the operating system.

Command:

sudo reboot

Equivalent command:

sudo systemctl reboot

Save your work before running this command.

---

## 9. shutdown -h now

Shuts down the system immediately.

Command:

sudo shutdown -h now

Explanation:

- shutdown - Schedules a shutdown.
- -h - Halt and power off the system.
- now - Perform the shutdown immediately.

Equivalent command:

sudo systemctl poweroff

Schedule a shutdown in 10 minutes:

sudo shutdown -h +10

Cancel a scheduled shutdown:

sudo shutdown -c

Warning: This command affects the entire machine, not only one service.

---

## 10. uptime

Displays how long the system has been running.

It also shows:

- Current time
- System uptime
- Number of logged-in users
- Load average for the last 1, 5, and 15 minutes

Command:

uptime

Example output:

10:42:18 up 3 days, 4:12, 2 users, load average: 0.08, 0.12, 0.10

Human-readable output:

uptime -p

Example:

up 3 days, 4 hours, 12 minutes

---

## 11. hostnamectl

Displays or changes the system hostname and operating system information.

Display system information:

hostnamectl

Display only the hostname:

hostnamectl hostname

Change the hostname:

sudo hostnamectl set-hostname my-server

Example:

sudo hostnamectl set-hostname web-server

---

# Common Service-Management Workflows

## Start a service now and at every boot

sudo systemctl enable --now nginx

## Stop a service now and prevent it from starting at boot

sudo systemctl disable --now nginx

## Restart a service and check its status

sudo systemctl restart nginx
systemctl status nginx

## Investigate a failed service

systemctl status nginx
sudo journalctl -u nginx -n 100 --no-pager

## Check whether a service is installed

systemctl list-unit-files | grep nginx

## List currently running services

systemctl list-units --type=service --state=running

## List all service units

systemctl list-units --type=service

## List failed services

systemctl --failed

---

# Example: Managing Nginx

## Start Nginx

sudo systemctl start nginx

## Stop Nginx

sudo systemctl stop nginx

## Restart Nginx

sudo systemctl restart nginx

## Enable Nginx at boot

sudo systemctl enable nginx

## Check Nginx status

systemctl status nginx

## View Nginx logs

sudo journalctl -u nginx

## Test the Nginx configuration

sudo nginx -t

## Reload Nginx

sudo systemctl reload nginx

---

# Quick Reference

sudo systemctl start nginx
    Start a service now

sudo systemctl stop nginx
    Stop a service now

sudo systemctl restart nginx
    Restart a service

sudo systemctl enable nginx
    Start a service automatically at boot

sudo systemctl disable nginx
    Prevent automatic startup at boot

systemctl status nginx
    Check service status

sudo journalctl -u nginx
    View service logs

sudo reboot
    Restart the system

sudo shutdown -h now
    Shut down the system immediately

uptime
    Show system uptime and load

hostnamectl
    Show hostname and system information

---

# Important Notes

- Use systemctl status first when a service fails.
- Use journalctl to find detailed error messages.
- enable and disable control automatic startup at boot.
- start and stop control the current service state.
- restart stops and starts the service again.
- reload reloads configuration without completely stopping the service.
- reboot restarts the entire operating system.
- shutdown -h now powers off the entire system.
- Always save your work before using reboot or shutdown.
- Replace nginx with the actual service name on your system.
