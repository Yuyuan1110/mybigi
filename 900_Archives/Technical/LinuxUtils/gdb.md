---
tags: 
  - Linux
  - Utils
  - gdb
  - debugger
  - c
alias: []
created: 2026-01-14
updated:
source:
---

# `gdb` Command Note

`gdb` (GNU Debugger) is the standard debugger for the GNU operating system. It allows you to see what is going on "inside" another program while it executes, or what another program was doing at the moment it crashed.

For more advanced usage, see [[gdb_advanced]].

## Preparation

Compile your program with the `-g` flag to include debugging symbols.

```bash
gcc -g main.c -o main_debug
```

## Basic Session

### 1. Start GDB

```bash
gdb ./main_debug
```

### 2. Set Breakpoints

Stop the program at specific lines or functions.

```gdb
(gdb) break main        # Stop at start of main()
(gdb) break 15          # Stop at line 15
```

### 3. Run the Program

```gdb
(gdb) run
# Or with arguments:
(gdb) run arg1 arg2
```

### 4. Stepping

- **`next` (n)**: Execute next line (step over functions).
- **`step` (s)**: Execute next line (step into functions).
- **`continue` (c)**: Continue execution until next breakpoint.

### 5. Inspecting Variables

```gdb
(gdb) print my_var      # Print value of variable
(gdb) print *ptr        # Print value pointed to by ptr
```

### 6. Quit

```gdb
(gdb) quit
```
