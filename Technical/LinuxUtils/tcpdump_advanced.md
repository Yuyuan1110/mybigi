---
tags: Linux, Utils, tcpdump, network, sniffing
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `tcpdump` Advanced Usage

This note covers more advanced `tcpdump` features. For a basic introduction, see [[tcpdump]].

## Combining Filters

You can combine filters using `and`, `or`, and `not` to create more specific capture criteria.

```bash
# Capture traffic from host 192.168.1.1 AND on port 443
sudo tcpdump -i eth0 host 192.168.1.1 and port 443

# Capture traffic on port 80 OR port 8080
sudo tcpdump -i eth0 port 80 or port 8080

# Capture all traffic except for SSH (port 22)
sudo tcpdump -i eth0 not port 22
```

## Reading from a File

Use the `-r` option to read and analyze a previously saved capture file.

```bash
# Read the capture.pcap file and apply a filter
tcpdump -r capture.pcap host 192.168.1.1
```

## Displaying Packet Contents

By default, `tcpdump` only shows packet headers. You can use flags to display the packet contents as well.

- **`-A`**: Display the packet contents in ASCII.
- **`-x`**: Display the packet contents in hex.
- **`-xx`**: Display the packet contents in hex, including the link-level header.

```bash
# Capture HTTP traffic and display the packet contents in ASCII
sudo tcpdump -i eth0 -A port 80
```

## Filtering by Packet Type

You can filter for specific protocols like `tcp`, `udp`, `icmp`, etc.

```bash
# Capture only ICMP (ping) packets
sudo tcpdump -i eth0 icmp

# Capture only TCP packets with the SYN flag set (connection requests)
sudo tcpdump -i eth0 'tcp[tcpflags] & tcp-syn != 0'
```

This last example shows the power of `tcpdump`'s filtering language, allowing you to inspect individual bits in the TCP header.