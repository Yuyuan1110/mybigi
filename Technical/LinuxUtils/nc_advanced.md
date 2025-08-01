---
tags: Linux, Utils, nc, network
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `nc` Advanced Usage

This note covers more advanced `nc` (netcat) features. For a basic introduction, see [[nc]].

## File Transfers

`nc` can be used for quick file transfers between machines.

**1. Send a File**

On the receiving machine, start `nc` in listen mode and redirect the output to a file:
```bash
# Receiver
nc -l 8888 > received_file.txt
```

On the sending machine, connect to the receiver and feed the file into `nc`:
```bash
# Sender
nc receiver_ip 8888 < original_file.txt
```

**Warning:** This method transfers data in the clear and is not secure. Use with caution on trusted networks.

## Port Scanning

While not as full-featured as `nmap`, `nc` can perform simple port scans.

```bash
# Scan a range of ports on a host
nc -vz -w 2 host.example.com 80-90
```
- **`-w <seconds>`**: Sets a timeout for connection attempts.

## Creating a Simple Chat Server

You can create a basic, two-way chat server.

**On the server:**
```bash
# Listen on port 8888
nc -l 8888
```

**On the client:**
```bash
# Connect to the server
nc server_ip 8888
```
Now, anything typed on either side will appear on the other.

## Using `nc` as a Proxy

`nc` can create a simple proxy to forward traffic.

```bash
# Create a listener on port 8080 that forwards to example.com on port 80
mkfifo /tmp/fifo
nc -l 8080 < /tmp/fifo | nc example.com 80 > /tmp/fifo
```
This creates a named pipe to shuttle data between two `nc` processes, effectively creating a TCP relay.