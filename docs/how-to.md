# How to use the Program

This chapter assumes that the code has been compiled and potentially installed already. Instructions on how to install and compile the code can be found in the [Compilation and Installation section](compilation-and-installation.md).

## Using the Program

We assume that you are in an directory from which you can run the program. For this section we assume that we are in the `build/` directory as explained in the [Compilation and Installation section](compilation-and-installation.md). If you have installed the software in a system path, you can follow the same steps, but the output printed and the paths used may differ.

The program can be run by

```bash
./documentationexample [YAMLFILE]
```

where `YAMLFILE` refers to the path of a YAML file, e.g., the file `config.yml` inside the `src/yamlParser/` directory. Specification of a `YAMLFILE` is *optional*.

The program will do the following steps

The program greets you with a message

```bash
Let's fight with CMake, Docker, and some dependencies!
```

The program modifies a flat set using Boost container and print the result

```bash
Modify a flat set using boost container
Elements in s1: 1       2       3       4
```

The program inspects the contens of the current directory and prints the contents of the directory to the screen.

```bash
Inspect the current directory using boost filesystem
"." is a directory containing:
    "CMakeCache.txt"
    "CMakeFiles"
    "Makefile"
    "cmake_install.cmake"
    "documentationexample"
    "libdocumentationexamplelib.a"
```

The program checks whether a `YAMLFILE` has been supplied on the command line.

If no `YAMLFILE` has been passed to the program.

If a `YAMLFILE` is specified, e.g., via

```bash
  ./documentationexample ../src/yamlParser/config.yml
```

the `YAMLFILE` will be parsed and the program tries to print the `version` property of the `YAMLFILE.

```bash
Parse some yaml file with yaml-cpp
  ../src/yamlParser/config.yml
Version: 1.2.3
```

If there is no `version` property, the program will crash

```bash
terminate called after throwing an instance of 'YAML::TypedBadConversion<std::__cxx11::basic_string<char, std::char_traits<char>, std::allocator<char> > >'
  what():  bad conversion
Aborted (core dumped
```

Finally, the program terminates.

### Full Output Without YAMLFILE

```bash
$ ./documentationexample
Let's fight with CMake, Docker, and some dependencies!

Modify a flat set using boost container
Elements in s1: 1       2       3       4

Inspect the current directory using boost filesystem
"." is a directory containing:
    "CMakeCache.txt"
    "CMakeFiles"
    "Makefile"
    "cmake_install.cmake"
    "documentationexample"
    "libdocumentationexamplelib.a"
```

### Full Output With YAMLFILE

```bash
$ ./documentationexample ../src/yamlParser/config.yml
Let's fight with CMake, Docker, and some dependencies!

Modify a flat set using boost container
Elements in s1: 1       2       3       4

Inspect the current directory using boost filesystem
"." is a directory containing:
    "CMakeCache.txt"
    "CMakeFiles"
    "Makefile"
    "cmake_install.cmake"
    "documentationexample"
    "libdocumentationexamplelib.a"

Parse some yaml file with yaml-cpp
  ../src/yamlParser/config.yml
Version: 1.2.3
```
