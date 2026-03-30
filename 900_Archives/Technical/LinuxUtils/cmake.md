---
tags: 
  - Linux
  - Utils
  - cmake
  - build
  - automation
alias: []
created: 2026-01-14
updated:
source:
---

# `cmake` Command Note

`cmake` is an open-source, cross-platform family of tools designed to build, test, and package software. It controls the compilation process using simple platform and compiler-independent configuration files (`CMakeLists.txt`), and generates native makefiles and workspaces that can be used in the compiler environment of your choice.

For more advanced usage, see [[cmake_advanced]].

## Basic Workflow

The standard `cmake` workflow involves:
1.  **Writing `CMakeLists.txt`**: Describing your project.
2.  **Configuration**: Generating the build system (e.g., Makefiles).
3.  **Build**: Compiling the code.

## The `CMakeLists.txt` File

Every directory in a CMake project usually contains a `CMakeLists.txt` file.

### Minimal Example

**`CMakeLists.txt`:**
```cmake
# Specify the minimum CMake version required
cmake_minimum_required(VERSION 3.10)

# Define the project name
project(HelloWorld)

# Create an executable from a source file
add_executable(hello main.c)
```

**`main.c`:**
```c
#include <stdio.h>
int main() { printf("Hello CMake!\n"); return 0; }
```

## Building the Project

It is best practice to perform "out-of-source" builds to keep your source directory clean.

**1. Create a Build Directory**
```bash
mkdir build
cd build
```

**2. Configure (Generate Build Files)**
Run `cmake` pointing to the source directory (usually `..`).
```bash
cmake ..
```
This generates a `Makefile` (on Linux) in the `build` directory.

**3. Build (Compile)**
You can use `make` directly, or let `cmake` call the build tool.
```bash
cmake --build .
```
Or simply:
```bash
make
```

**4. Run**
```bash
./hello
```

## Handling Multiple Files

```cmake
cmake_minimum_required(VERSION 3.10)
project(MyProject)

# Add multiple source files to the executable
add_executable(my_app main.c utils.c config.c)
```

