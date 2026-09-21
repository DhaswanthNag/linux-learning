# 🌐 Linux Networking Commands

> A beginner-friendly reference for checking network information, testing connectivity, transferring files, and troubleshooting networks in Linux.

---

## 📋 Commands at a Glance

| Command | Purpose | Example |
|---|---|---|
| `ip a` | Show IP addresses and interfaces | `ip a` |
| `ping` | Test network connectivity | `ping google.com` |
| `traceroute` | Trace route to a host | `traceroute google.com` |
| `ss` | Show socket/network connections | `ss -tuln` |
| `curl` | Transfer data from/to a server | `curl example.com` |
| `wget` | Download files from the web | `wget file.zip` |
| `ssh` | Connect to a remote system | `ssh user@ip` |
| `scp` | Securely copy files | `scp file.txt user@ip:/path` |
| `netstat` | Show network connections | `netstat -tuln` |
| `hostname` | Show system hostname | `hostname` |
| `dig` | Perform DNS lookup | `dig google.com` |

---

## 🌐 1. `ip a` — Show IP Addresses

Displays network interfaces and their IP addresses.

```bash
ip a
```

Show a specific interface:

```bash
ip addr show eth0
```

---

## 📡 2. `ping` — Test Connectivity

Checks whether a host is reachable.

```bash
ping google.com
```

Stop with:

```text
Ctrl + C
```

---

## 🛣️ 3. `traceroute` — Trace Network Route

Shows the route packets take to a destination.

```bash
traceroute google.com
```

> ℹ️ On Ubuntu, install if needed:

```bash
sudo apt install traceroute
```

---

## 🔌 4. `ss` — Show Network Connections

Displays active sockets and listening ports.

```bash
ss -tuln
```

Common options:

```text
-t → TCP
-u → UDP
-l → Listening
-n → Numeric addresses
```

---

## 🌍 5. `curl` — Transfer Data

Fetches data from a URL.

```bash
curl example.com
```

Download a file:

```bash
curl -O https://example.com/file.zip
```

---

## ⬇️ 6. `wget` — Download Files

Downloads files from the internet.

```bash
wget https://example.com/file.zip
```

---

## 🔐 7. `ssh` — Secure Remote Login

Connects to another Linux system securely.

```bash
ssh user@192.168.1.10
```

Example:

```bash
ssh user@example.com
```

---

## 📦 8. `scp` — Secure File Copy

Copies files between systems securely.

Copy to remote system:

```bash
scp file.txt user@192.168.1.10:/home/user/
```

Copy from remote system:

```bash
scp user@192.168.1.10:/home/user/file.txt .
```

---

## 📊 9. `netstat` — Network Statistics

Displays network connections and listening ports.

```bash
netstat -tuln
```

> ℹ️ `netstat` may not be installed by default. Modern Linux systems commonly use `ss`.

---

## 🖥️ 10. `hostname` — Show Hostname

Displays the system's hostname.

```bash
hostname
```

Show hostname and related information:

```bash
hostnamectl
```

---

## 🔎 11. `dig` — DNS Lookup

Queries DNS information for a domain.

```bash
dig google.com
```

Short result:

```bash
dig google.com +short
```

---

## 🧪 Mini Practice

```bash
ip a

ping google.com

ss -tuln

curl example.com

hostname

dig google.com
```

---

## 🛡️ Safety Tips

- Do not share private IP addresses or credentials unnecessarily.
- Be careful when connecting to unknown SSH servers.
- Verify remote paths before using `scp`.
- Do not download unknown files with `wget` or `curl`.
- Use `ss` to inspect listening ports.
- Stop continuous commands like `ping` with `Ctrl + C`.

---

## 📌 Quick Revision

```text
ip a         → Show IP addresses
ping         → Test connectivity
traceroute   → Trace network route
ss           → Show network connections
curl         → Transfer data
wget         → Download files
ssh          → Remote login
scp          → Secure file copy
netstat      → Network statistics
hostname     → Show hostname
dig          → DNS lookup
```

---

## 📚 References

- [Linux man-pages](https://man7.org/linux/man-pages/)
- [GNU Wget](https://www.gnu.org/software/wget/)
- [OpenSSH](https://www.openssh.com/)
- [curl](https://curl.se/)

---

⭐ If this guide helped you learn Linux, consider starring the repository!

Made for Linux beginners with 🐧 and ❤️