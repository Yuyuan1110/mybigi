---
tags: 
  - Linux
  - Utils
  - make
  - build
  - automation
alias: []
created: 2026-01-14
updated:
source:
---

# `make` Advanced Usage

This note covers more advanced `make` features. For a basic introduction, see [[make]].

## Functions

`make` has built-in functions for text processing and file manipulation.

### 1. `wildcard`

Finds files matching a pattern.

```makefile
# Get a list of all .c files in the current directory
SRCS = $(wildcard *.c)
```

### 2. `patsubst`

Performs pattern substitution.

```makefile
# Convert the list of .c files (SRCS) into a list of .o files
OBJS = $(patsubst %.c, %.o, $(SRCS))
```

### 3. `shell`

Executes a shell command and returns the output.

```makefile
# Get the current date
DATE = $(shell date +%Y-%m-%d)
```

## Advanced Logic

### 1. Conditional Execution

You can use `ifeq`, `ifneq`, `ifdef`, and `ifndef`.

```makefile
DEBUG = 1

ifeq ($(DEBUG), 1)
    CFLAGS += -g
else
    CFLAGS += -O2
endif
```

### 2. Include Other Makefiles

Useful for modularizing complex builds.

```makefile
include config.mk
```

## Parallel Execution

You can speed up builds by running commands in parallel.

```bash
# Run up to 4 jobs in parallel
make -j4
```

## Recursive Make

For projects with subdirectories, you can call `make` recursively.

**Root `Makefile`:**
```makefile
SUBDIRS = src lib

.PHONY: all $(SUBDIRS)

all: $(SUBDIRS)

$(SUBDIRS):
	$(MAKE) -C $@
```
This enters each subdirectory and runs `make` inside it.

## Example: A Complete Generic Makefile

This Makefile automatically finds all `.c` files, compiles them, and handles dependencies.

```makefile
CC = gcc
CFLAGS = -Wall -Wextra -g
LDFLAGS = 

# Find all source files
SRCS = $(wildcard *.c)
# Generate object file names
OBJS = $(patsubst %.c, %.o, $(SRCS))
# The final executable name
TARGET = my_app

.PHONY: all clean

all: $(TARGET)

$(TARGET): $(OBJS)
	$(CC) $(LDFLAGS) $^ -o $@

# Pattern rule for object files
%.o: %.c
	$(CC) $(CFLAGS) -c $< -o $@

clean:
	rm -f $(OBJS) $(TARGET)
```
