---
tags: C, Programming, Compiler, gcc
alias: []
created: 2025-08-01
updated:
source:
---

# `gcc` Advanced Usage

This note covers more advanced `gcc` features. For a basic introduction, see [[gcc]].

## Controlling the Compilation Process

You can stop the compilation process at any stage.

- **`-E`**: Stop after the preprocessing stage. This is useful for debugging macros.
- **`-S`**: Stop after the compilation stage and generate assembly code.
- **`-c`**: Stop after the assembly stage and generate an object file (`.o`).

**Examples:**

```bash
# Preprocess hello.c and output the result to stdout
gcc -E hello.c

# Compile hello.c to assembly code (creates hello.s)
gcc -S hello.c

# Compile hello.c to an object file (creates hello.o)
gcc -c hello.c
```

Compiling to object files is the standard way to build larger projects. You compile each source file into an object file, and then link the object files together.

```bash
# Compile source files into object files
gcc -c main.c
gcc -c greeter.c

# Link the object files to create the final executable
gcc main.o greeter.o -o greeter_app
```

## Warnings and Errors

`gcc` can provide detailed warnings about potential issues in your code.

- **`-Wall`**: Enables most common warnings.
- **`-Wextra`**: Enables even more warnings.
- **`-Werror`**: Treats all warnings as errors, forcing you to fix them.

```bash
# Compile with all common warnings enabled
gcc -Wall hello.c -o hello
```

## Optimization Levels

`gcc` can optimize your code for performance.

- **`-O0`**: No optimization (the default).
- **`-O1`**: Basic optimization.
- **`-O2`**: More optimization.
- **`-O3`**: The highest level of optimization.
- **`-Os`**: Optimize for size.

```bash
# Compile with the highest level of optimization
gcc -O3 my_program.c -o my_program
```

## Linking External Libraries

Use the `-l` option to link against external libraries.

```bash
# Link against the math library (libm)
gcc my_math_program.c -o my_math_program -lm
```

- **`-L`**: Specifies a directory to search for libraries.

```bash
# Search for libraries in the /usr/local/lib directory
gcc my_program.c -L/usr/local/lib -lcustom
```
