---
tags: 
  - Linux
  - Utils
  - gdb
  - debugger
alias: []
created: 2026-01-14
updated:
source:
---

# `gdb` Advanced Usage

This note covers more advanced `gdb` features. For a basic introduction, see [[gdb]].

## Examining Memory and Stack

### Backtrace (`bt`)

See the call stack (which functions called which).

```gdb
(gdb) bt
#0  func3 () at main.c:30
#1  func2 () at main.c:20
#2  main () at main.c:10
```

- **`frame 1`**: Switch to stack frame 1 (caller).

### Examining Memory (`x`)

Examine memory at a specific address.

```gdb
# Examine 10 integers in hex format at address of 'array'
(gdb) x/10x &array
```

## Watchpoints

Stop execution when a variable's value *changes* (hardware watchpoint).

```gdb
(gdb) watch my_variable
```

## Conditional Breakpoints

Stop only if a condition is true.

```gdb
(gdb) break loop_handler if i == 100
```

## Text User Interface (TUI)

GDB has a built-in visual mode.

- **`layout src`**: Show source code split.
- **`layout asm`**: Show assembly split.
- **`Ctrl+x` `a`**: Toggle TUI mode.

## Core Dumps

Debug a program that crashed.

1.  Enable core dumps: `ulimit -c unlimited`
2.  Run program (it crashes and produces `core` file).
3.  Debug it:

```bash
gdb ./my_app core
```
Inside GDB, use `bt` to see where it crashed.
