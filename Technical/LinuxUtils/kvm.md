---
tags: 
  - Linux
  - Utils
  - kvm
  - virtualization
  - kernel
alias: []
created: 2026-01-14
updated:
source:
---

# `kvm` Command Note

KVM (Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It turns the Linux kernel into a hypervisor.

**Note:** KVM itself is a kernel module. You usually interact with it via userspace tools like **QEMU**, **libvirt** (`virsh`), or **GNOME Boxes**.

For advanced tuning, see [[kvm_advanced]].

## Checking for Support

Before using KVM, verify your CPU supports it.

### 1. Check CPU Flags

```bash
# Result > 0 indicates support
egrep -c '(vmx|svm)' /proc/cpuinfo
```
- **vmx**: Intel VT-x
- **svm**: AMD-V

### 2. Use `kvm-ok`

The `cpu-checker` package provides a helper script.

```bash
sudo kvm-ok
```
Output should be: `KVM acceleration can be used`.

## Enabling KVM

### 1. Load Modules

Usually loaded automatically, but you can check:

```bash
lsmod | grep kvm
```

### 2. User Permissions

To run VMs without root, add your user to the `kvm` group.

```bash
sudo usermod -aG kvm $USER
newgrp kvm
```

## Usage with QEMU

The most common "raw" usage is adding the `-enable-kvm` (or `-accel kvm`) flag to QEMU.

```bash
qemu-system-x86_64 -enable-kvm ...
```
Without this flag, QEMU uses software emulation, which is significantly slower.
