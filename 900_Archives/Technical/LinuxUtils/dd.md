---
tags:
  - Linux
  - Utils
  - dd
  - disk
  - imaging
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `dd` Command Note

`dd` is a command-line utility for copying and converting files. It is often used for tasks like creating disk images, cloning drives, and writing bootable USB drives.

**Warning:** `dd` is a powerful tool. Be very careful with the `if` (input file) and `of` (output file) options, as a mistake can lead to data loss.

For more advanced usage, see [[dd_advanced]].

## Basic Usage: Copying Data

The basic syntax for `dd` is:

```bash
dd if=<source> of=<destination> [options]
```

- **`if`**: Input file. The source of the data.
- **`of`**: Output file. The destination for the data.

### Basic Examples

**1. Creating a Disk Image**

This will create an image of the `/dev/sda` disk and save it to a file.

```bash
# Be sure to replace /dev/sda with the correct disk
sudo dd if=/dev/sda of=~/disk_image.img
```

**2. Writing an ISO to a USB Drive**

This will write a Linux ISO file to a USB drive, making it bootable.

```bash
# Be sure to replace /dev/sdX with the correct USB drive
sudo dd if=~/Downloads/ubuntu.iso of=/dev/sdX
```

**3. Creating a File of a Specific Size**

This can be useful for creating swap files or for testing.

```bash
# Create a 1GB file filled with zeros
dd if=/dev/zero of=~/large_file.img bs=1G count=1
```
- **`bs`**: Block size. The size of each chunk of data to copy.
- **`count`**: The number of blocks to copy.