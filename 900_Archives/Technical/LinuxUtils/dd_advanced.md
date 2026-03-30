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

# `dd` Advanced Usage

This note covers more advanced `dd` features. For a basic introduction, see [[dd]].

## Monitoring Progress

By default, `dd` does not show any progress information. You can use the `status=progress` option to see real-time statistics.

```bash
sudo dd if=/dev/sda of=~/disk_image.img status=progress
```

## Data Conversion

`dd` can convert data on the fly using the `conv` option.

- **`conv=ucase`**: Convert text to uppercase.
- **`conv=lcase`**: Convert text to lowercase.
- **`conv=swab`**: Swap every pair of input bytes.

**Example:**

```bash
# Convert a file to uppercase
echo "hello world" | dd conv=ucase
# Output: HELLO WORLD
```

## Error Handling

When reading from a failing disk, you can tell `dd` to continue on errors.

- **`conv=noerror`**: Continue after read errors.
- **`conv=sync`**: Pad input blocks with zeros if there was a read error. This keeps the output file the same size as the input.

```bash
# Create a disk image from a failing drive, ignoring errors
sudo dd if=/dev/sdb of=~/recovered_image.img conv=noerror,sync
```

## Combining `dd` with Other Tools

`dd` can be used in pipelines with other commands.

**1. Create a Compressed Disk Image**

This will create a compressed image of a disk on the fly.

```bash
sudo dd if=/dev/sda | gzip > ~/disk_image.img.gz
```

**2. Wipe a Drive with Random Data**

This will overwrite a drive with random data from `/dev/urandom`.

```bash
# Warning: This will destroy all data on the drive
sudo dd if=/dev/urandom of=/dev/sdX bs=4M status=progress
```
