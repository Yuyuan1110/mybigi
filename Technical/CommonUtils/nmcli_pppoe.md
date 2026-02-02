---
tags: 
  - Linux
  - Utils
  - nmcli
  - pppoe
  - network
alias: []
created: 2026-02-02
updated: 2026-02-02
source:
---

# `nmcli` PPPoE Setup Note

This note covers how to set up and manage PPPoE (Point-to-Point Protocol over Ethernet) connections using `nmcli`.

For basic `nmcli` usage, see [[nmcli]].

## Create PPPoE Connection

### 1. Using Command Line (Non-interactive)

You can add a PPPoE connection directly with one command. Note that providing the password in the command line might expose it in your shell history.

```bash
nmcli connection add \
  type pppoe \
  con-name "MyPPPoE" \
  ifname eth0 \
  username "your_username" \
  password "your_password"
```
- **`type pppoe`**: Specifies the connection type.
- **`con-name`**: The name you want to give to this connection profile.
- **`ifname`**: The physical interface to use (e.g., `eth0`, `enp3s0`).
- **`username`**: Your ISP-provided username.
- **`password`**: Your ISP-provided password.

### 2. Using Interactive Mode (Safer)

This method avoids putting the password in the shell history.

```bash
nmcli connection edit type pppoe con-name "MyPPPoE"
```

Inside the interactive prompt (`nmcli>`):
```bash
set pppoe.username your_username
set pppoe.password your_password
save
quit
```

## Manage PPPoE Connection

### Start the connection
```bash
nmcli connection up MyPPPoE
```

### Stop the connection
```bash
nmcli connection down MyPPPoE
```

### Delete the connection
```bash
nmcli connection delete MyPPPoE
```

## Troubleshooting

- **Check status**: `nmcli connection show MyPPPoE`
- **View logs**: `journalctl -u NetworkManager` or `tail -f /var/log/syslog` (on some systems).
- **Verify interface**: Ensure the physical interface (e.g., `eth0`) is up but not necessarily configured with an IP.

