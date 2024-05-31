In C++, the order in which libraries are specified during the linking process can be critical, particularly when using static libraries. This dependency on order stems primarily from the way the linker resolves symbols (i.e., function and variable names) from the libraries. Here’s a detailed look at why the order matters:

### How Linkers Work

Linkers are responsible for combining object files (.o, .obj) and libraries into a single executable or library. During this process, they resolve references to symbols that are defined in other object files or libraries.

1. **Symbol Resolution Process**: When the linker encounters a symbol in one object file that is undefined, it searches for a definition of this symbol in the subsequent object files and libraries mentioned in the command line. If the definition is found, the linker uses it to resolve the symbol and then moves on.

2. **Single-Pass Linking**: Traditionally, linkers make a single pass through the objects and libraries from the order they are listed on the command line. If a library that resolves a symbol appears before the object file that needs it, the linker won't backtrack to resolve these symbols once it moves past them. This is the primary reason why the order can matter.

### Practical Example

Suppose you have two libraries:

- `libmath.a` contains a function `add()`
- `libutil.a` contains a function `calculate()` that calls `add()`

If you link these libraries in the order `-lutil -lmath`, the linker processes `libutil.a` first and doesn't find `add()`. When it processes `libmath.a`, it includes `add()`, but since it doesn’t backtrack, it doesn’t resolve the `add()` needed by `libutil.a`, leading to an unresolved symbol error.

However, linking with `-lmath -lutil` would work because when `libutil.a` is processed, `add()` has already been defined by `libmath.a`.

### When Does Order Not Matter?

1. **Dynamic Linking**: With dynamic libraries (.so, .dll), the order is less critical because unresolved symbols can be resolved at runtime by the dynamic linker. This allows a more flexible handling of symbol resolution compared to static linking.

2. **Modern Tooling**: Some modern linkers and build systems are smarter or can be configured to make multiple passes or handle dependencies more gracefully. For instance, using linker flags like `--start-group` and `--end-group` in GNU linker can mitigate the order issue by instructing the linker to handle groups of libraries differently, making multiple passes if necessary.

3. **Automatic Dependency Resolution**: Some build systems, like CMake, can automatically determine the correct order of libraries based on the dependencies specified in the project configuration, relieving the developer of the burden to manually specify the correct order.

Understanding how your tools handle linking and their capabilities can help you manage complex projects more effectively and avoid common pitfalls related to library ordering and symbol resolution.