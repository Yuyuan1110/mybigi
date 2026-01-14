---
tags: 
  - Linux
  - Utils
  - nc
  - network
  - diag
  - diagnostic
  - diagnostics
  - diagnosis
alias: []
created: 2025-07-08
updated: 2025-08-01
source:
---

# `nc` Command Note
`nc` (netcat) is a versatile networking utility for reading from and writing to network connections using TCP or UDP.

For more advanced usage, see [[nc_advanced]].

## Command Basic Usage

### Client Mode: Connecting to a Server

Command format:
```bash
nc [options] [hostname] [port]
```

**Options:**
- **`-v`**: Verbose output, showing connection progress.
- **`-z`**: Zero-I/O mode. Scans for listening daemons without sending any data.

**Example: Checking a Port**
```bash
# Check if a web server is listening on port 80
nc -vz example.com 80
# Expected output on success: Connection to example.com 80 port [tcp/*] succeeded!
```

**Example: Sending Data**
```bash
# Connect to a server and send a simple message
echo "Hello Server" | nc localhost 8888
```

### Server Mode: Listening for Connections

Command format:
```bash
nc -l [port]
```

**Options:**
- **`-l`**: Listen mode, waits for incoming connections.

**Example: Creating a Simple Server**
```bash
# Listen on port 8888 for an incoming connection
nc -l 8888
# Any data sent from a client will be printed to standard output.
```
