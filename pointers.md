# Welcome To Pointers


## Why should we use pointers?
- pointers help us manage and access memory at a lower level
- they store memory addresses which let us dynamically alter memory size and location
## What is a Pointer?
- a pointer is a variable that holds the memory address of another variable
- instead of storing a direct value, the pointer stores the address of where that value is located in memory

```C
int x = 10; // x is defined as the intiger of 10
int *p = &x; // *p is defined as the memory address of x
```

## Declaring A Pointer
- to declare a pointer, we use the `*` symbol

```C
int *p;
double *q;
char *r;

// all of these pointers are holding the memory addresses for all the variables
```

## Dynamic Memory Allocation

### Malloc - Memory Allocation
- mallos is used to allocate a specific amount of memory in bytes
- returns a pointer to the start, but if the allocation fails it returns a null value
- the memory allocated with mallos is *not initialized* 

```C
int *ptr = (int *)malloc(size_in_bytes);
int *arr = (int *)malloc(5 * sizeof(int)); 
// allocated memory for 5 intigers
```

### Calloc - Contiguous Allocation
- calloc stand for **Contiguous Allocation** and usef to allocate memory for an array of elements, initializing all the bits to 0
- taking two arguements: the number oe elements and teh size of each element. returns a pointer to the beginning of the block
- calloc is mainly used while working with arrays tomavoud unexpected syntax

```C
int *ptr = (int *)calloc(num_elements, element_size);
int *arr = (int *)calloc(5, sizeof(int));
```

### Realloc - Reallocation
- used to resize the previously allocated memory block without loosing its data
- taking arguements and a pointer to the current memeory block, and the new size to be reformed in bytes
- can expand or shrink memory blocks
- copies the data to a new location.
- returns null if failed, but does not affect the original block

```C
int *new_ptr = (int *)realloc(old_ptr, new_size_in_bytes)
```

