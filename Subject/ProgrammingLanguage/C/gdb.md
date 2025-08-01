---
tags: C, Programming, Debugger, gdb
alias: []
created: 2025-08-01
updated:
source:
---

# `gdb` Command Note

`gdb` (The GNU Debugger) is a powerful tool for finding and fixing bugs in programs. It allows you to pause a program's execution, inspect the state of variables, and step through the code line by line.

For more advanced usage, see [[gdb_advanced]].

## Compiling for Debugging

To use `gdb` effectively, you must compile your program with debugging symbols. Use the `-g` flag with `gcc`.

```bash
# Compile hello.c with debug symbols
gcc -g hello.c -o hello_debug
```

## Basic GDB Session

**1. Start GDB**

Load your compiled program into `gdb`.

```bash
gdb ./hello_debug
```
This will start the `gdb` interactive shell.

**2. Set a Breakpoint**

A breakpoint tells `gdb` to pause the program at a specific location.

```gdb
# Set a breakpoint at the beginning of the main function
(gdb) break main

# Set a breakpoint at a specific line number (e.g., line 5)
(gdb) break 5
```

**3. Run the Program**

Use the `run` command to start the program. It will execute until it hits a breakpoint.

```gdb
(gdb) run
```

**4. Stepping Through Code**

Once paused, you can execute the program line by line.

- **`next` (or `n`)**: Execute the next line of code. If the line is a function call, it executes the entire function without stepping into it.
- **`step` (or `s`)**: Execute the next line of code. If the line is a function call, it steps *into* the function, allowing you to debug it.

**5. Inspecting Variables**

Use the `print` command to see the value of a variable.

```gdb
# Print the value of the variable 'x'
(gdb) print x
```

**6. Continuing Execution**

Use the `continue` (or `c`) command to resume normal execution until the next breakpoint is hit or the program finishes.

```gdb
(gdb) continue
```

**7. Quitting GDB**

Use the `quit` (or `q`) command to exit the debugger.

```gdb
(gdb) quit
```
