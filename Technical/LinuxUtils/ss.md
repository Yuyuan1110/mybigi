---
tags: 
  - Linux
  - Utils
  - ss
  - network
  - netstat
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `ss` Command Note

The `ss` command is a modern utility for investigating sockets. It has replaced the older `netstat` command and is generally faster and provides more detailed information.

For more advanced usage, see [[ss_advanced]].

## Command Basic Usage

`ss` can display statistics for TCP, UDP, and other types of sockets.

Command format:
```bash
ss [options]
```

### Basic Examples

**1. List All Connections**

By default, `ss` lists open non-listening sockets that have established a connection.

```bash
# Show a list of all established connections
ss
```

**2. List Listening Sockets**

Use the `-l` or `--listening` option to show sockets that are listening for incoming connections.

```bash
# Show all listening sockets
ss -l
```

**3. List All TCP Sockets**

Use the `-t` or `--tcp` option to display only TCP sockets.

```bash
# Show all TCP sockets (both listening and established)
ss -t -a
```
- **`-a`** or **`--all`**: Displays both listening and non-listening sockets.

**4. List All UDP Sockets**

Use the `-u` or `--udp` option to display only UDP sockets.

```bash
# Show all UDP sockets
ss -u -a
```

**5. Show Process Information**

Use the `-p` or `--processes` option to see which process is using a socket.

```bash
# Show listening TCP sockets with the process name
ss -ltp
```
