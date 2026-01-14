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

# `cmake` Advanced Usage

This note covers more advanced `cmake` features. For a basic introduction, see [[cmake]].

## Libraries

CMake makes it easy to create and link libraries.

### Creating a Library

```cmake
# Create a static library named "mathlib" from math.c
add_library(mathlib STATIC math.c)

# Create a shared library
# add_library(mathlib SHARED math.c)
```

### Linking a Library

```cmake
add_executable(calculator main.c)

# Link "mathlib" to the "calculator" executable
target_link_libraries(calculator PUBLIC mathlib)
```

## Include Directories

If your headers are in a separate folder (e.g., `include/`), you need to tell CMake where to find them.

```cmake
# Add "include" directory to the search path for headers
target_include_directories(calculator PUBLIC "${CMAKE_CURRENT_SOURCE_DIR}/include")
```

## Finding External Packages

Use `find_package` to locate system libraries (like OpenSSL, Boost, etc.).

```cmake
# Find the OpenSSL package
find_package(OpenSSL REQUIRED)

add_executable(secure_app main.c)

# Link OpenSSL libraries
target_link_libraries(secure_app OpenSSL::SSL OpenSSL::Crypto)
```

## Variables and Cache

You can define variables to control the build.

```cmake
# Set the C standard to C11
set(CMAKE_C_STANDARD 11)

# Define a custom variable
set(MY_VAR "SomeValue")
```

**Cache Variables** are stored in `CMakeCache.txt` and can be set from the command line.

```bash
# Set a build type (Debug, Release, RelWithDebInfo, MinSizeRel)
cmake -DCMAKE_BUILD_TYPE=Release ..
```

## Specifying Generators

CMake supports various build systems (Generators).

- **Unix Makefiles** (Default on Linux)
- **Ninja** (Fast, highly recommended)

```bash
# Generate Ninja build files instead of Makefiles
cmake -G Ninja ..
ninja
```

## Subdirectories

For larger projects, organize code into subfolders.

**Root `CMakeLists.txt`:**
```cmake
cmake_minimum_required(VERSION 3.10)
project(BigProject)

# Add the 'src' subdirectory
add_subdirectory(src)
```

**`src/CMakeLists.txt`:**
```cmake
add_executable(main main.c)
```
