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

# `ss` Advanced Usage

This note covers more advanced `ss` features. For a basic introduction, see [[ss]].

## Filtering by State

`ss` allows you to filter sockets by their TCP state (e.g., `established`, `syn-sent`, `time-wait`).

```bash
# Show all TCP sockets in the 'established' state
ss -t state established

# Show all TCP sockets in a 'time-wait' state
ss -t state time-wait
```

## Filtering by Port Number

You can filter for connections based on the destination or source port.

- **`dport`**: Destination port
- **`sport`**: Source port

```bash
# Show connections to a specific destination port (e.g., HTTPS)
ss -t dport = :443

# Show connections from a specific source port
ss -t sport = :22

# You can also use operators
ss -t dport > :1024
```

## Using IP Addresses

You can filter by IP address to see connections to or from a specific host.

```bash
# Show all connections to the IP address 192.168.1.5
ss dst 192.168.1.5

# Show all connections from the IP address 192.168.1.5 on a specific port
ss src 192.168.1.5:22
```

## Displaying Socket Timers

The `-o` or `--options` flag shows timer information associated with a socket, which is useful for debugging connection issues.

```bash
# Show timer information for TCP sockets
ss -to
```

## Getting a Summary of Sockets

The `-s` or `--summary` flag provides a quick overview of socket statistics.

```bash
# Display a summary of all sockets
ss -s
```
This will show the total number of connections, broken down by protocol and TCP state.