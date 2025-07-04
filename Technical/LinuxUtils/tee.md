---
tags: Linux, Utils, tee, grep
alias: []
created: 2025-07-02
updated:
source:
---
# `tee` command note
`tee` command can output message to std output and write it to file at the same time.

## `tee` command basic usage

Command format:
```bash
command |tee [option] file...
```

Common Option:
`-a`, `--append`: Writing output message to tail of the file, instead overwrite.
`-i`, `--ignore-interrupts`: If use this option, command will not be interrupted, even use `ctrl-c`, `tee` will continue to the end of process.
`--help`: Some help information.
`--version`: Version information.

Example:
```bash
ls -l |tee file.txt # it will show ls info at std and write it to file.txt, like '>', it file.txt is exist, it will be overwrite.

dmesg |tee -a file1.txt # show dmesg at the std output and write it to file1.txt, like '>>', if file is exist, it will append at the tail, if not, it will created.

cat /var/log/message.log |tee file1.txt file2.txt file3.txt # it can write to mutiple file.

cat /etc/sysctl.conf |sudo tee /some/where/need/root/permission/to/write # where different between '>' and tee is tee can get root perssion by sudo.
```