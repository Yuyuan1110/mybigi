---
tags: 
  - Linux
  - Utils
  - clang
  - compiler
  - llvm
  - analysis
alias: []
created: 2026-01-14
updated:
source:
---

# `clang` Advanced Usage

This note covers more advanced `clang` features. For a basic introduction, see [[clang]].

## Static Analysis

Clang has a built-in static analyzer that can find bugs that the compiler might miss (like memory leaks or logic errors).

```bash
# Run the static analyzer
clang --analyze main.c
```
This typically produces an HTML report if run with `scan-build`, or prints text output.

## Sanitizers

Clang (and modern GCC) includes "Sanitizers" – fast, runtime detectors for bugs.

### 1. AddressSanitizer (ASan)
Detects memory errors like out-of-bounds accesses, use-after-free, and memory leaks.

```bash
# Compile with ASan
clang -fsanitize=address -g main.c -o main_asan

# Run the program
./main_asan
```
If the program has a memory error, ASan will print a detailed report and exit.

### 2. UndefinedBehaviorSanitizer (UBSan)
Detects undefined behavior like integer overflow, null pointer dereference, etc.

```bash
clang -fsanitize=undefined -g main.c -o main_ubsan
```

## Cross-Compilation

Clang is inherently a cross-compiler. You don't need separate binaries for different targets (unlike GCC).

```bash
# Compile for Windows (64-bit) from Linux
clang --target=x86_64-pc-windows-gnu main.c -o main.exe
```

## LLVM Tools

Clang works with other LLVM tools:

- **`clang-format`**: Automatically formats code.
  ```bash
  clang-format -i main.c
  ```
- **`clang-tidy`**: A linter that checks for style violations and bugs.
  ```bash
  clang-tidy main.c -- -Iinclude
  ```
