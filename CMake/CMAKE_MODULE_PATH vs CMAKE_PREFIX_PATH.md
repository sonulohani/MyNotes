`CMAKE_MODULE_PATH` and `CMAKE_PREFIX_PATH` are two important variables in CMake that influence how it finds packages, modules, and other resources. Here’s a breakdown of what each is used for and how they differ:

### CMAKE_MODULE_PATH
- **Purpose**: `CMAKE_MODULE_PATH` is used to specify one or more directories where CMake should look for custom `find` modules. These modules typically contain instructions on how to locate and configure dependencies (libraries, headers, and other files) that are not automatically found by CMake.
- **Usage**: You add paths to `CMAKE_MODULE_PATH` when you need CMake to find custom or non-standard packages via `find_package()` that are not in its default module path. This variable directly affects only the searching of CMake modules, not the libraries or executables.
- **Setting**: It’s often set in the `CMakeLists.txt` file to ensure that the project’s specific find modules are always available.

Example:
```cmake
list(APPEND CMAKE_MODULE_PATH "${CMAKE_SOURCE_DIR}/cmake/modules")
```

### CMAKE_PREFIX_PATH
- **Purpose**: `CMAKE_PREFIX_PATH` helps CMake locate external libraries, executables, and other files. It is used by `find_package()`, `find_library()`, `find_file()`, and other similar commands that search for specific resources. The paths specified in `CMAKE_PREFIX_PATH` are expected to follow the standard directory structure (`include`, `lib`, etc.).
- **Usage**: This variable is crucial when you have dependencies installed in non-standard locations (not in `/usr/local`, etc.) and you need to point CMake to these locations.
- **Setting**: `CMAKE_PREFIX_PATH` can be set in either `CMakeLists.txt`, `CMakePresets.json`, or as an environment variable, depending on whether the path needs to be shared across projects or specific to a single configuration.

Example:
```cmake
set(CMAKE_PREFIX_PATH "/path/to/custom/library")
```

### Key Differences
- **Scope**: `CMAKE_MODULE_PATH` affects where CMake looks for its `find` modules, which are scripts that define how to find and configure dependencies. `CMAKE_PREFIX_PATH` influences the actual search paths for libraries, headers, and other components that these `find` modules or CMake’s automatic searching mechanism might look for.
- **Impact**: Modifying `CMAKE_MODULE_PATH` changes where CMake searches for the module scripts (the `.cmake` files defining the find logic), while adjusting `CMAKE_PREFIX_PATH` changes the root directories used to find actual software components across the system.

### Choosing Which to Set
Choose `CMAKE_MODULE_PATH` when you need to provide custom or additional module scripts for finding dependencies. Opt for `CMAKE_PREFIX_PATH` when you know the dependencies are in specific locations and you need to help CMake in locating these libraries or executables. Both settings can be used together if your project has dependencies in non-standard locations and requires custom find scripts to locate them properly.