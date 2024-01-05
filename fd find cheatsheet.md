Ah, got it! fdfind is an abbreviation for fd, which is a fast and user-friendly alternative to find. Here's a cheatsheet for fd:

### Basic Usage:

1. Search for a file or directory by name:
   ```bash
   fd <pattern>
   ```

2. Search in a specific directory:
   ```bash
   fd <pattern> /path/to/directory
   ```

3. Case-insensitive search:
   ```bash
   fd -i <pattern>
   ```

### Filtering and Options:

4. Search for a pattern in specific file types:
   ```bash
   fd -e <extension>
   ```

5. Exclude files/directories from search:
   ```bash
   fd --exclude <pattern>
   ```

6. Search for hidden files:
   ```bash
   fd --hidden <pattern>
   ```

### Output Control:

7. Display only directories:
   ```bash
   fd -t d <pattern>
   ```

8. Display only files:
   ```bash
   fd -t f <pattern>
   ```

9. Limit search depth:
   ```bash
   fd --max-depth <depth> <pattern>
   ```

### Advanced Usage:

10. Print full paths:
    ```bash
    fd -P <pattern>
    ```

11. Execute a command on each result:
    ```bash
    fd <pattern> -x command {}
    ```

12. Follow symbolic links:
    ```bash
    fd -L <pattern>
    ```

13. Search for files changed within a time range:
    ```bash
    fd --changed-within <time>
    ```

### Performance and Optimization:

14. Parallel search using multiple threads:
    ```bash
    fd <pattern> --threads <num>
    ```

15. Optimize for large directories:
    ```bash
    fd <pattern> --max-results <num>
    ```

16. Output path relative to the search directory:
    ```bash
    fd --relative-path <pattern>
    ```

These are just some common use cases for fd. For more detailed information, you can refer to the official documentation (`man fd` or fd --help).
