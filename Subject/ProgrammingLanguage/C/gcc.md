---
tags: C, Programming, Compiler, gcc
alias: []
created: 2025-08-01
updated:
source:
---

# `gcc` Command Note

`gcc` (GNU Compiler Collection) is the standard compiler for most Unix-like operating systems. It can compile C, C++, Objective-C, and other languages.

This note focuses on compiling C programs.

For more advanced usage, see [[gcc_advanced]].

## Basic Compilation Steps

Compiling a C program with `gcc` involves four main stages:

1.  **Preprocessing**: Processes macros and include files (`#include`).
2.  **Compilation**: Translates the C code into assembly language.
3.  **Assembly**: Converts the assembly code into machine code (object files).
4.  **Linking**: Combines the object files with necessary libraries to create an executable.

## Command Basic Usage

### Compiling a Single File

The simplest way to use `gcc` is to compile a single source file into an executable.

**1. Create a C file (`hello.c`):**
```c
#include <stdio.h>

int main() {
    printf("Hello, world!\n");
    return 0;
}
```

**2. Compile the file:**
```bash
gcc hello.c
```
This will create an executable file named `a.out` by default.

**3. Run the executable:**
```bash
./a.out
```

### Specifying the Output File

Use the `-o` option to specify a name for the output file.

```bash
# Compile hello.c and create an executable named 'hello'
gcc hello.c -o hello
```

### Compiling Multiple Files

If your program is split across multiple files, you can compile them all at once.

**`main.c`:**
```c
#include <stdio.h>
#include "greeter.h"

int main() {
    greet();
    return 0;
}
```

**`greeter.c`:**
```c
#include <stdio.h>

void greet() {
    printf("Hello from the greeter!\n");
}
```

**`greeter.h`:**
```c
void greet();
```

**Compile all `.c` files together:**
```bash
gcc main.c greeter.c -o greeter_app
```

