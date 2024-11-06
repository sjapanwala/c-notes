### Detailed Notes on Advanced Usage of Pointers in C

### 1. **Dynamic Memory Allocation**

- Dynamic memory allocation allows the size of data structures to change during runtime.
- Commonly used for strings, arrays, and structures.

### 2. **Memory Allocation Functions**

- **malloc**: Allocates a block of memory without initialization. Usage example:
    
    ```c
    
    int *p = malloc(n * sizeof(int));  // Allocates space for n integers
    
    ```
    
- **calloc**: Allocates and initializes a block of memory to zero. Usage example:
    
    ```c
    
    int *p = calloc(n, sizeof(int));  // Allocates space for n integers initialized to 0
    ```
    
- **realloc**: Resizes previously allocated memory without losing existing data. Usage example:
    
    ```c
    p = realloc(p, new_size);  // Resizes the memory block pointed to by p
    ```
    

### 3. **Null Pointers**

- A null pointer indicates that memory allocation failed. It’s essential to check for null after allocation to avoid dereferencing a null pointer.

### 4. **Memory Deallocation**

- **free**: Used to deallocate memory previously allocated by `malloc`, `calloc`, or `realloc` to prevent memory leaks.
    
    ```c
    free(p);  // Deallocates memory pointed to by 
    ```
    

### 5. **Memory Leaks**

- Occurs when memory is allocated but not freed. This can lead to a program consuming more memory over time, eventually causing crashes.

### 6. **Reallocation**

- If `realloc` fails, it returns `NULL`, leaving the original memory block unchanged. Always assign the result of `realloc` to a temporary pointer before assigning it back to avoid losing reference to the original memory.