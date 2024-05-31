In CMake, `add_compile_definitions` is a command that allows you to add preprocessor definitions to your build. These definitions can then be used in your source code, typically to enable or disable features, or to make certain settings available globally across your codebase.

### Usage of `add_compile_definitions`

The syntax for `add_compile_definitions` is straightforward. You specify the definitions that you want to add, and they will automatically be added to the compile command line as `-D` flags (or their equivalent, depending on the compiler being used). Here's how you can use it:

```cmake
add_compile_definitions(DEFINITION1 DEFINITION2=VALUE)
```

### Example `CMakeLists.txt`

Here’s a practical example that demonstrates how to use `add_compile_definitions` in a CMake project:

```cmake
cmake_minimum_required(VERSION 3.12)  # Ensures proper support for add_compile_definitions
project(MyProject)

# Add a compile definition globally
add_compile_definitions(MY_DEFINE)

# Add a compile definition with a value
add_compile_definitions(VERSION=3)

# Create an executable
add_executable(myexecutable main.cpp)

# Alternatively, to apply definitions to a specific target, use target_compile_definitions
target_compile_definitions(myexecutable PRIVATE FEATURE_ENABLE)
```

### Example `main.cpp`

The corresponding `main.cpp` might look like this, utilizing the preprocessor definitions set in the `CMakeLists.txt`:

```cpp
#include <iostream>

int main() {
    #ifdef MY_DEFINE
    std::cout << "MY_DEFINE is set" << std::endl;
    #endif

    std::cout << "Version is " << VERSION << std::endl;

    #ifdef FEATURE_ENABLE
    std::cout << "Feature enable is defined." << std::endl;
    #endif

    return 0;
}
```

### Explanation

- `add_compile_definitions`: This command is used in the `CMakeLists.txt` to define preprocessor macros. `MY_DEFINE` is defined without a value, and `VERSION` is defined with a value `3`.
    
- `target_compile_definitions`: This command applies definitions to a specific target rather than globally. In the example, `FEATURE_ENABLE` is defined for the `myexecutable` target only. Definitions can have different scopes like `PRIVATE`, `INTERFACE`, or `PUBLIC`:
    
    - `PRIVATE`: Definitions are added to the target only. They are not available to any other targets that link against this one.
    - `PUBLIC`: Definitions are added to the target and propagate to any targets that link against this one.
    - `INTERFACE`: Definitions are not added to the target where they are declared but are used on targets that link against this one.

### Choosing Between `add_compile_definitions` and `target_compile_definitions`

- **Use `add_compile_definitions`** when you want to apply definitions globally to all targets in the directory and its subdirectories (affected by this `CMakeLists.txt` or included subdirectories).
- **Use `target_compile_definitions`** when you want to apply definitions specifically to a single target, with control over propagation to linked targets.

This distinction is crucial for managing large projects with multiple targets where you might want to isolate definitions to specific parts of your application or library.
