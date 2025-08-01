---
tags: Linux, Utils, perf, performance, profiling
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `perf` Command Note

`perf` is a powerful performance analysis tool in Linux. It can be used for performance monitoring, profiling, and tracing.

For more advanced usage, see [[perf_advanced]].

## Basic Usage: Profiling a Command

The most common use of `perf` is to profile a command and see where it spends its time.

**1. Record Performance Data**

Use `perf record` to run a command and collect performance data.

```bash
# Profile the 'ls' command
perf record ls
```
This will create a `perf.data` file in the current directory.

**2. View the Report**

Use `perf report` to view the collected data.

```bash
perf report
```
This will open an interactive interface showing the functions where the program spent the most time.

## Counting System-Wide Events

`perf stat` can be used to count events for a command or for the entire system.

**1. Count Events for a Command**

```bash
# Count performance statistics for the 'ls' command
perf stat ls
```
This will output statistics like cycles, instructions, and cache misses.

**2. Count System-Wide Events**

```bash
# Count CPU cycles and instructions for the entire system for 5 seconds
perf stat -a sleep 5
```

## Listing Available Events

`perf list` shows all the events that can be monitored on your system.

```bash
perf list
```
This is useful for finding specific events to trace, such as cache misses or branch prediction failures.