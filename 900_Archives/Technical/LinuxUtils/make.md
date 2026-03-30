---
tags:
  - Linux
  - Utils
  - make
  - build
  - automation
alias: []
created: 2025-08-01
updated: 2026-01-14
source:
---

# `make` Command Note

`make` is a build automation tool that automatically builds executable programs and libraries from source code by reading files called `Makefiles` which specify how to derive the target program.

For more advanced usage, see [[make_advanced]].

## Why Use `make`?

In a large project, compiling everything every time you make a small change is inefficient. `make` solves this by understanding the dependencies between files. It only recompiles a file if its source code or any of the files it depends on have changed since the last compilation.

## Core Concepts of a `Makefile`

A `Makefile` consists of a set of *rules*. A rule has three parts: a target, prerequisites, and a command.

```makefile
<target>: <prerequisites>
	<command>
```

- **Target**: The file you want to create (e.g., an object file `.o` or an executable).
- **Prerequisites** (or Dependencies): The files that the target depends on.
- **Command**: The shell command to execute to create the target. **This line must start with a Tab character, not spaces.**

--- 

## Basic Usage

### 1. A Simple Example

Let's start with a single C file, `hello.c`.

**`Makefile`:**
```makefile
hello: hello.c
	gcc hello.c -o hello
```

To build the executable, simply run:
```bash
make
```
`make` will look for the first target (`hello`), see that it depends on `hello.c`, and run the command.

### 2. Handling Multiple Files

Consider a project with `main.c`, `greeter.c`, and `greeter.h`.

**`Makefile`:**
```makefile
# The final executable
greeter_app: main.o greeter.o
	gcc main.o greeter.o -o greeter_app

# Build main.o
main.o: main.c greeter.h
	gcc -c main.c

# Build greeter.o
greeter.o: greeter.c greeter.h
	gcc -c greeter.c
```

When you run `make`, it will build the dependencies (`main.o` and `greeter.o`) first, and then link them. If you modify `greeter.c` and run `make` again, only `greeter.o` and `greeter_app` will be rebuilt.

### 3. Using Variables

Variables make Makefiles maintainable.

```makefile
CC = gcc
CFLAGS = -Wall -g
TARGET = greeter_app
OBJS = main.o greeter.o

# The default target
all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) $(OBJS) -o $(TARGET)

main.o: main.c greeter.h
	$(CC) $(CFLAGS) -c main.c

# Phony target for cleaning up
clean:
	rm -f $(TARGET) $(OBJS)
```

- **Variables**: Defined at the top (e.g., `CC = gcc`). Referenced with `$(CC)`.
- **Phony Target**: `clean` is not a file. It's a command to clean up.

### 4. Automatic Variables

- **`$@`**: The target name.
- **`$^`**: All prerequisites.
- **`$<`**: The first prerequisite.

```makefile
# Pattern rule: How to build .o from .c
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@
```
