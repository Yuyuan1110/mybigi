---
tags: 
  - Linux
  - Utils
  - tcpdump
  - network
  - sniffing
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `tcpdump` Command Note

`tcpdump` is a powerful command-line packet analyzer. It allows you to capture and inspect network traffic on a specific network interface.

For more advanced usage, see [[tcpdump_advanced]].

## Basic Usage: Capturing Packets

Running `tcpdump` requires root privileges.

**1. List Network Interfaces**

Use the `--list-interfaces` flag to see the available network interfaces.

```bash
sudo tcpdump --list-interfaces
```

**2. Start Capturing**

Use the `-i` option to specify an interface to capture on.

```bash
# Capture packets on the eth0 interface
sudo tcpdump -i eth0
```

Press `Ctrl+C` to stop capturing.

### Basic Filtering

`tcpdump` can filter traffic based on various criteria.

- **`host`**: Capture traffic to or from a specific host.
- **`port`**: Capture traffic on a specific port.
- **`net`**: Capture traffic to or from a specific network.

**Examples:**

```bash
# Capture traffic from the host 192.168.1.1
sudo tcpdump -i eth0 host 192.168.1.1

# Capture traffic on port 80 (HTTP)
sudo tcpdump -i eth0 port 80

# Capture traffic from the 10.0.0.0/8 network
sudo tcpdump -i eth0 net 10.0.0.0/8
```

## Saving Captures to a File

Use the `-w` option to save the captured packets to a file for later analysis.

```bash
# Capture packets and save them to a file named 'capture.pcap'
sudo tcpdump -i eth0 -w capture.pcap
```

This file can be analyzed with `tcpdump` or other tools like Wireshark.