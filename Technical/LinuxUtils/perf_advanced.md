---
tags: Linux, Utils, perf, performance, profiling
alias: []
created: 2025-08-01
updated: 2025-08-01
source:
---

# `perf` Advanced Usage

This note covers more advanced `perf` features. For a basic introduction, see [[perf]].

## Flame Graphs

Flame graphs are a visualization of profiled software, allowing the most frequent code paths to be identified quickly and accurately. `perf` can be used with other tools to generate them.

**1. Install FlameGraph Tools**
```bash
git clone https://github.com/brendangregg/FlameGraph
cd FlameGraph
```

**2. Capture Stack Traces**
```bash
# Profile a command and capture call graphs
perf record -F 99 -g -- <your_command>
```
- **`-F 99`**: Sample at 99 Hertz.
- **`-g`**: Capture call graphs.

**3. Generate the Flame Graph**
```bash
perf script | ./stackcollapse-perf.pl | ./flamegraph.pl > flamegraph.svg
```
Open the `flamegraph.svg` file in a web browser to view the interactive flame graph.

## Tracing Kernel Events

`perf trace` is similar to `strace`, but with more features and less overhead. It can be used to trace system calls and other kernel events.

```bash
# Trace system calls for the 'ls' command
perf trace ls
```

## Annotating Code

`perf annotate` can be used to see the assembly code and performance data side-by-side.

```bash
# Record data for a specific command
perf record ./my_program

# Annotate the code
perf annotate
```
This will show the disassembled code with the percentage of time spent on each instruction.

## Top-Down Performance Analysis

`perf top` provides a real-time view of the functions that are currently using the most CPU time.

```bash
# Run perf top to see a live view of system performance
perf top
```
This is useful for identifying performance bottlenecks in real-time.