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

# `gcc` Advanced Usage

This note covers more advanced `gcc` features. For a basic introduction, see [[gcc]].

## Compilation Stages

You can stop `gcc` at intermediate stages using flags:

1.  **Preprocessing (`-E`)**: Expands macros and includes.
    ```bash
    gcc -E main.c > main.i
    ```
2.  **Compilation (`-S`)**: Generates Assembly (`.s`).
    ```bash
    gcc -S main.c
    ```
3.  **Assembly (`-c`)**: Generates Object files (`.o`).
    ```bash
    gcc -c main.c
    ```

## Optimization

`gcc` offers various optimization levels:

- **`-O0`**: No optimization (default, best for debugging).
- **`-O1`**, **`-O2`**: Moderate optimization.
- **`-O3`**: Aggressive optimization (may increase binary size or compilation time).
- **`-Os`**: Optimize for size.

```bash
gcc -O2 main.c -o main
```

## Debugging Symbols

Use `-g` to include debugging information for tools like `gdb`.

```bash
gcc -g main.c -o main_debug
```

## Include and Library Paths

- **`-I<dir>`**: Add a directory to the header search path.
- **`-L<dir>`**: Add a directory to the library search path.

```bash
# Look for headers in ./include and libraries in ./lib
gcc -I./include -L./lib main.c -o main -lmylib
```

## Defines

Define macros from the command line.

```bash
# Equivalent to #define DEBUG 1 in the code
gcc -DDEBUG=1 main.c -o main
```
