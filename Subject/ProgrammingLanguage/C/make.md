---
tags: C, Programming, Build, make, Makefile
alias: []
created: 2025-08-01
updated:
source:
---

# `make` and `Makefile` Note

`make` is a build automation tool that automatically builds executable programs and libraries from source code by reading files called `Makefiles` which specify how to derive the target program.

## Why Use `make`?

In a large project, compiling everything every time you make a small change is inefficient. `make` solves this by understanding the dependencies between files. It only recompiles a file if its source code or any of the files it depends on have changed since the last compilation. This saves a significant amount of time.

## Core Concepts of a `Makefile`

A `Makefile` consists of a set of *rules*. A rule has three parts: a target, prerequisites, and a command.

```makefile
<target>: <prerequisites>
	<command>
```

- **Target**: The file you want to create, typically an object file (`.o`) or an executable.
- **Prerequisites** (or Dependencies): The files that the target depends on. These files must exist before the command is run.
- **Command**: The shell command to execute to create the target. **This line must start with a Tab character, not spaces.**

--- 

## A Simple Example

Let's start with a single C file, `hello.c`.

**`Makefile`:**
```makefile
hello: hello.c
	gcc hello.c -o hello
```

To build the executable, you simply run the `make` command in the same directory:
```bash
make
```
`make` will look for the `hello` target, see that it depends on `hello.c`, and run the `gcc` command to create it.

## A More Realistic Example

Consider a project with `main.c`, `greeter.c`, and `greeter.h`.

**`Makefile`:**
```makefile
# The final executable we want to build
greeter_app: main.o greeter.o
	gcc main.o greeter.o -o greeter_app

# Rule to build main.o
main.o: main.c greeter.h
	gcc -c main.c

# Rule to build greeter.o
greeter.o: greeter.c greeter.h
	gcc -c greeter.c
```

When you run `make`, it will:
1.  Try to build `greeter_app` (the first target is the default).
2.  See that `greeter_app` depends on `main.o` and `greeter.o`.
3.  Build `main.o` by running `gcc -c main.c` because it depends on `main.c`.
4.  Build `greeter.o` by running `gcc -c greeter.c` because it depends on `greeter.c`.
5.  Finally, link the two object files together to create `greeter_app`.

If you then change `greeter.c` and run `make` again, it will only recompile `greeter.o` and then re-link `greeter_app`. `main.o` will not be recompiled.

--- 

## Using Variables

Makefiles become much more powerful and maintainable with variables.

```makefile
# Define variables
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

greeter.o: greeter.c greeter.h
	$(CC) $(CFLAGS) -c greeter.c

# Phony target for cleaning up
clean:
	rm -f $(TARGET) $(OBJS)
```

- **Variables**: `CC` (C Compiler), `CFLAGS` (Compiler Flags), `TARGET`, and `OBJS` (Object files) are defined at the top. You reference them with `$(VAR_NAME)`.
- **Phony Target**: A target that is not a file. `clean` is a common phony target to remove generated files. We declare it as phony to prevent `make` from getting confused if a file named `clean` ever exists.
  ```makefile
  .PHONY: all clean
  ```

## Automatic Variables

`make` provides special, automatic variables to simplify rules.

- **`$@`**: The name of the target.
- **`$^`**: The names of all prerequisites.
- **`$<`**: The name of the first prerequisite.

Let's rewrite the previous `Makefile` using automatic variables:

```makefile
CC = gcc
CFLAGS = -Wall -g
TARGET = greeter_app
OBJS = main.o greeter.o

.PHONY: all clean

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(CFLAGS) $^ -o $@

# A pattern rule for compiling .c files to .o files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(TARGET) $(OBJS)
```

The rule `%.o: %.c` is a *pattern rule*. It tells `make` how to create any `.o` file from a corresponding `.c` file. This single rule replaces all the individual rules for `main.o` and `greeter.o`, making the `Makefile` much cleaner and easier to extend.