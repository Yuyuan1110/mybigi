---
tags: Linux, Utils, tee
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `tee` Advanced Usage

This note covers more advanced `tee` features. For a basic introduction, see [[tee]].

## Writing to a Privileged File

One of the most common advanced uses for `tee` is writing to a file that requires root permissions.

A command like `sudo echo "..." > /etc/config.conf` will fail because the redirection (`>`) is handled by your user's shell, not by `sudo`.

`tee` solves this by running as the root user and handling the file writing itself.

```bash
# Correct way to write to a file owned by root
echo "kernel.domainname = example.com" | sudo tee /etc/sysctl.d/99-domain.conf

# Append a line to a privileged file
echo "127.0.0.1 my-app.local" | sudo tee -a /etc/hosts
```

## Ignoring Interrupts

The `-i` option tells `tee` to ignore interrupt signals like `Ctrl+C`. This can be useful in scripts where you want to ensure the output is fully written to the file even if the process is interrupted.

```bash
# The output of the long-running command will be written to the log
# even if you interrupt it with Ctrl+C.
./long_running_script.sh | tee -i output.log
```

## Combining with Other Commands

`tee` is a powerful tool for building complex command pipelines. You can use it to save intermediate results while still passing the data along.

```bash
# 1. Get a list of running processes
# 2. Save the full list to a file
# 3. Filter for a specific process (e.g., 'sshd')
ps aux | tee all_processes.txt | grep sshd
```
In this example, `all_processes.txt` will contain the complete output of `ps aux`, while your terminal will only show the lines containing `sshd`.