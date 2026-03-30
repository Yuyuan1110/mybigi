---
tags: 
  - Linux
  - Utils
  - kvm
  - virtualization
  - performance
alias: []
created: 2026-01-14
updated:
source:
---

# `kvm` Advanced Usage

This note covers advanced KVM configuration and tuning, primarily for performance. For basic setup, see [[kvm]].

## Nested Virtualization

Nested virtualization allows you to run a Virtual Machine *inside* another Virtual Machine.

### 1. Enable on Host (Intel)

```bash
# Temporarily
sudo modprobe -r kvm_intel
sudo modprobe kvm_intel nested=1

# Permanently
echo "options kvm_intel nested=1" | sudo tee /etc/modprobe.d/kvm.conf
```

### 2. Enable on Host (AMD)

```bash
echo "options kvm_amd nested=1" | sudo tee /etc/modprobe.d/kvm.conf
```

### 3. Verify

```bash
cat /sys/module/kvm_intel/parameters/nested
# Output should be 'Y' or '1'
```

## Performance Tuning

### Hugepages

Using Hugepages reduces memory management overhead for large VMs.

```bash
# Reserve hugepages (e.g., 1024 pages of 2MB each)
echo 1024 | sudo tee /proc/sys/vm/nr_hugepages
```
When using QEMU/KVM, point the memory to the hugepages path (`-mem-path /dev/hugepages`).

### CPU Pinning

Pinning vCPUs (virtual CPUs) to specific physical CPUs prevents context switching overhead. This is usually configured in higher-level tools like Libvirt (`virsh edit <domain>`), but concepts apply to KVM scheduling.

```xml
<!-- Example Libvirt XML snippet for pinning -->
<vcpu placement='static'>2</vcpu>
<cputune>
  <vcpupin vcpu='0' cpuset='2'/>
  <vcpupin vcpu='1' cpuset='3'/>
</cputune>
```
