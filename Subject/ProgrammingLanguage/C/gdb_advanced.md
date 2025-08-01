---
tags: C, Programming, Debugger, gdb
alias: []
created: 2025-08-01
updated:
source:
---

# `gdb` Advanced Usage

This note covers more advanced `gdb` features. For a basic introduction, see [[gdb]].

## Conditional Breakpoints

You can set a breakpoint that only triggers when a certain condition is true.

```gdb
# Break at line 10 only if the variable 'i' is equal to 5
(gdb) break 10 if i == 5
```

## Watchpoints

A watchpoint will stop the program whenever the value of a variable changes.

```gdb
# Stop the program whenever the value of 'my_var' changes
(gdb) watch my_var
```

## Examining the Call Stack

The call stack shows the chain of function calls that led to the current point in the program.

- **`backtrace` (or `bt`)**: Show the full call stack.
- **`up`**: Move one frame up the call stack.
- **`down`**: Move one frame down the call stack.

This is invaluable for figuring out how you got into a particular state.

```gdb
(gdb) backtrace
#0  my_function (x=10) at main.c:15
#1  0x000055555555523a in main () at main.c:25
```

## Changing Variable Values

You can modify variables on the fly to test different scenarios.

```gdb
# Change the value of 'x' to 20
(gdb) set var x = 20
```

## GDB Text User Interface (TUI)

GDB has a Text User Interface (TUI) that can show the source code, assembly, and command window in a terminal.

- **`Ctrl+x` `a`**: Toggle TUI mode on and off.
- **`Ctrl+x` `2`**: Show the source code and command window.
- **`Ctrl+x` `s`**: Show the source code and assembly.

This provides a more visual debugging experience directly in the terminal.

## Running Commands on Break

You can automate `gdb` by telling it to run a series of commands whenever it hits a specific breakpoint.

```gdb
# Select breakpoint 1
(gdb) commands 1

# Define commands to run for this breakpoint
> silent
> print x
> print y
> continue
> end
```
In this example, whenever breakpoint 1 is hit, `gdb` will silently print the values of `x` and `y` and then immediately continue execution.