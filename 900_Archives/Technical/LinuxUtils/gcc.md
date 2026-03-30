---
tags: 
  - Linux
  - Utils
  - gcc
  - compiler
  - c
alias: []
created: 2026-01-14
updated:
source:
---

# `gcc` Command Note

`gcc` (GNU Compiler Collection) is the standard compiler for most Unix-like operating systems. It supports C, C++, and other languages.

For more advanced usage, see [[gcc_advanced]].

## Basic Usage

### 1. Compile a Single File

```bash
# Compile hello.c -> a.out (default)
gcc hello.c

# Compile and run
./a.out
```

### 2. Specify Output File

Use `-o` to name the executable.

```bash
gcc hello.c -o hello
```

### 3. Compile Multiple Files

```bash
gcc main.c utils.c -o my_app
```

### 4. Enable Warnings

It is best practice to enable warnings to catch bugs early.

- **`-Wall`**: Enable all common warnings.

```bash
gcc -Wall main.c -o main
```

### 5. Link Libraries

Use `-l` to link shared libraries (e.g., math library `libm`).

```bash
# Link with math library (-lm)
gcc main.c -o main -lm
```
