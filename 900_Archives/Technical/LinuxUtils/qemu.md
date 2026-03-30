---
tags: 
  - Linux
  - Utils
  - qemu
  - virtualization
  - emulation
alias: []
created: 2026-01-14
updated:
source:
---

# `qemu` Command Note

QEMU is a generic and open-source machine emulator and virtualizer. When used as a machine emulator, QEMU can run OSes and programs made for one machine (e.g., an ARM board) on a different machine (e.g., your own PC). When used with KVM, it runs guest code directly on the host CPU for near-native performance.

For advanced usage, see [[qemu_advanced]].

## Basic Usage

### 1. Creating a Disk Image

Use `qemu-img` to create virtual hard drives.

```bash
# Create a 20GB qcow2 image
qemu-img create -f qcow2 mydisk.qcow2 20G
```
- **qcow2**: QEMU Copy On Write format (grows as data is written).

### 2. Booting an ISO (Installation)

```bash
qemu-system-x86_64 \
  -enable-kvm \
  -m 2G \
  -smp 2 \
  -hda mydisk.qcow2 \
  -cdrom ubuntu.iso \
  -boot d
```
- **`-enable-kvm`**: **Crucial** for performance (uses hardware virtualization).
- **`-m 2G`**: Assign 2GB RAM.
- **`-smp 2`**: Assign 2 CPU cores.
- **`-hda`**: The hard disk image.
- **`-cdrom`**: The installation ISO.
- **`-boot d`**: Boot from CD-ROM first.

### 3. Running an Installed VM

After installation, simply remove the `-cdrom` and `-boot` flags.

```bash
qemu-system-x86_64 \
  -enable-kvm \
  -m 2G \
  -smp 2 \
  -hda mydisk.qcow2
```
