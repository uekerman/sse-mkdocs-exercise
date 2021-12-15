# Compilation and Installation

This section shortly describes the dependencies needed to compile the software and the individual steps to compile the code.

## Dependencies

- C++ compiler
- CMake at least version 3.12
- Boost containers and Boost filesystem at least version 1.65.1
- yaml-cpp at least version 0.6.0

## Compiling the code

We assume that you are in the root of the repository. Then execute the following steps:

1. Create a new directory, e.g., called `build/`, and change into this directory

   ```bash
   mkdir -p build && cd build
   ```

2. Configure the project

   ```bash
   cmake ..
   ```

3. Build the project

   ```bash
   make
   ```

   This will create the executable (also referred to as program) `documentationexample` and the static library `libdocumentationexamplelib.a`. Now, you can use the program already from within this `build/` directory.

4. (Optional) Install the software on your system

   ```bash
   make install
   ```

   You might have to use `sudo` to install the software if it should be installed in one of the system paths.

More information about how to use the program can be found in the [How to use the Program section](how-to.md).