---
tags: 
  - Linux
  - Utils
  - nmcli
  - network
alias: []
created: 2026-02-02
updated: 2026-02-02
source:
---

# `nmcli` Command Note

`nmcli` is a command-line tool for controlling NetworkManager and reporting network status. It can be used to create, display, edit, delete, activate, and deactivate network connections, as well as control and display network device status.

For PPPoE specific setup, see [[nmcli_pppoe]].

## Command Basic Usage

Command format:
```bash
nmcli [OPTIONS] OBJECT { COMMAND | help }
```

### Common Objects
- **`device` (d)**: Manage network interfaces.
- **`connection` (c)**: Manage NetworkManager's connections.
- **`networking` (n)**: Overall networking control.
- **`general` (g)**: General NetworkManager status and operations.

### Basic Examples

**1. Show General Status**

```bash
nmcli general status
```

**2. List All Network Devices**

```bash
# Show status of all network interfaces
nmcli device status
```

**3. Show Details for a Specific Device**

```bash
# Replace 'eth0' with your interface name
nmcli device show eth0
```

**4. List All Network Connections**

```bash
# Show all configured connections
nmcli connection show
```

**5. Activate/Deactivate a Connection**

```bash
# Activate a connection
nmcli connection up id <connection_name>

# Deactivate a connection
nmcli connection down id <connection_name>
```

**6. Wi-Fi Management**

```bash
# List available Wi-Fi access points
nmcli device wifi list

# Connect to a Wi-Fi network
nmcli device wifi connect <SSID> password <password>
```

**7. Networking Control**

```bash
# Turn networking off
nmcli networking off

# Turn networking on
nmcli networking on
```
