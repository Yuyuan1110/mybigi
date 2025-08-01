---
tags: Linux, Utils, tee
alias: []
created: 2025-07-02
updated: 2025-08-01
source:
---

# `tee` Command Note

The `tee` command reads from standard input and writes to both standard output and one or more files, effectively splitting the output.

For more advanced usage, see [[tee_advanced]].

## Command Basic Usage

Command format:
```bash
command | tee [OPTION] [FILE]...
```

**Options:**
- **`-a`**: Append to the given files, do not overwrite.

### Basic Examples:

**1. Save and View Command Output**
```bash
# List files, view the output, and save it to a file named 'listing.txt'
ls -l | tee listing.txt
```

**2. Append Output to a Log File**
```bash
# Run a script and append its output to a log file, while still seeing it on screen
./my_script.sh | tee -a script.log
```

**3. Write to Multiple Files**
```bash
# Send the output of 'dmesg' to two separate files
dmesg | tee dmesg.log dmesg_backup.log
```
