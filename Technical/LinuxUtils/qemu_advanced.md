---
tags: 
  - Linux
  - Utils
  - qemu
  - virtualization
  - networking
alias: []
created: 2026-01-14
updated:
source:
---

# `qemu` Advanced Usage

This note covers advanced QEMU features like networking, snapshots, and virtio. For basics, see [[qemu]].

## Virtio Drivers (Performance)

By default, QEMU emulates legacy hardware (like IDE disks and Realtek network cards) for compatibility. For performance, use paravirtualized "Virtio" devices.

```bash
qemu-system-x86_64 \
  -enable-kvm \
  -drive file=mydisk.qcow2,if=virtio \
  -net nic,model=virtio \
  -net user
```
**Note:** Windows guests require installing Virtio drivers manually.

## Networking

### User Networking (Default)
The VM can access the internet, but the host cannot initiate connections to the VM easily.

### Port Forwarding
Map a host port to a guest port to access services (e.g., SSH).

```bash
# Forward Host Port 2222 -> Guest Port 22
-net nic,model=virtio -net user,hostfwd=tcp::2222-:22
```
Now you can SSH into the guest via `ssh -p 2222 user@localhost`.

## Snapshots

QEMU (specifically qcow2) supports internal snapshots.

### Saving a Snapshot (Monitor)
While the VM is running, switch to the QEMU Monitor (`Ctrl+Alt+2`) or use the `-monitor stdio` flag.

```
(qemu) savevm my_snapshot
```

### Loading a Snapshot

```
(qemu) loadvm my_snapshot
```

### Managing Snapshots with `qemu-img`

```bash
# List snapshots
qemu-img snapshot -l mydisk.qcow2

# Apply a snapshot (revert disk state)
qemu-img snapshot -a my_snapshot mydisk.qcow2

# Delete a snapshot
qemu-img snapshot -d my_snapshot mydisk.qcow2
```

## Headless Mode (VNC)

To run a VM without a GUI window (e.g., on a server), use `-nographic` or `-vnc`.

```bash
# Expose display via VNC on :0 (port 5900)
qemu-system-x86_64 ... -vnc :0
```
Connect with a VNC viewer to `localhost:5900`.

