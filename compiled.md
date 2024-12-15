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

- If `realloc` fails, it returns `NULL`, leaving the original memory block unchanged. Always assign the result of `realloc` to a temporary pointer before assigning it back to avoid losing reference to the original memory.### Detailed Notes on Advanced Usage of Pointers in C

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
xx
### 4. **Memory Deallocation**

- **free**: Used to deallocate memory previously allocated by `malloc`, `calloc`, or `realloc` to prevent memory leaks.
    
    ```c
    free(p);  // Deallocates memory pointed to by 
    ```
    

### 5. **Memory Leaks**

- Occurs when memory is allocated but not freed. This can lead to a program consuming more memory over time, eventually causing crashes.

### 6. **Reallocation**

- If `realloc` fails, it returns `NULL`, leaving the original memoray block unchanged. Always assign the result of `realloc` to a temporary pointer before assigning it back to avoid losing reference to the original memory.

# Pointers and arrays in C

## arrays
- arrays and pointers in c are very closely related,

```C
int a[10] // this creates an array with 10 properties, but thy are all zeros
int *p; // this creates a pointer to an intiger
p = &a[3]; // this creates a pointer to the mem address to the fourth element in array a
*p = 5; // this is exactly the same thing as writing a[3] = 5, because we are assing the intiger 5 to the memory address of the fourth value in the array. since the pointer has the same value, they are equal

// a[3] = 5 == *p = 5
```
## Pointer Arithmetic - ***GETS CONFUSING FAST***
- think of memory in an array like this
```txt
Array a:  [ ][ ][ ][5][ ][ ][ ][ ][ ][ ]
                  ^
                  p points here
```
- if intigers are 4 bytes long, then
- p + 1 adds 4 bytes to the memory address
- p + 2 adds 8 bytes to the memory address
- p - 1 removes 4 bytes from the memory address
- so in reality if we look at it in the sense of an array, it moves up and down and array

## Names of Arrays can actually be used as pointers
```c
int a[10];
int *p = a;

/* notice how we didnt include an address symbol '&' here.
* because a is automatically a pointer, that points to the first element
*/
```

### But keep this in mind
- you cannot change where `a` points to , it will always point to the start of the array
- but if we appoint p to a, then we can copy the memory addressess and point increment p through the array

```c
// all of these are equivalent ways to access array elements
a[5] = 10;     // this directly assigns the arrays 6th element to 10
*(a + 5) = 10; // this uses pointer arithmetic to add a[0] + a[5] to go to a[5]
*(p + 5) = 10; // this assumes that p is a pointer pointing to the start of array a
p[5] = 10;     // this subscribes the 5, kind of linking back to array == pointers
```
## **THINGS TO AVOID**
- these should be avoideed, because they can crash your program, or cause memory leaks
```c
int a[10]
int *p = &a[0];
p = p + 20;
*p =  5;

/* this is very dangerous
* we are creating a pointer to the start of the array
* but we are adding incrementing by by 20 places
but since our array is only 10 elements long, we are going out of range */
```

## Using Pointers and Arrays to create a summation
```c
int sum = 0;
int *p;
for (p =&a[0]; p < &a[N]; p++) {
    sum += *p; 
}
/* walk through
* we initialize the variabke 'sum'
* we create a pointer, '*p' which will be used to iterate through the array
* for loop psudo code
*   'p = &a[0]' sets the pointer mem address to the start of an array
*   'p < &a[N]' checking is p is less than the address of the element one past the last element of the array,
*   'p++'       increments the position of p, to go to the next element
```

# Practice Questions
```c
int arr[5] = {1,2,3,4,5};
int *p = &arr[2]
*p = 10;
```
- we are setting an array to have 5 elements, and all those elements are the values in range (0,5].
- then we create a pointer to the memory address of the third element in the array
- then we change the pointers value from previous value to the value of 10
- so the array's state after looks like `arr = 1,2,10,4,5` 

```c
int arr[5] = {1, 2, 3, 4, 5};
int *p = arr;
p = p + 2;
*p = 7;
p--;
*p = 6;
```
- first we are creating an array with 5 elements and we are setting the values to be the range of (0,5]
- we create a pointer and appoint it to the array, that sets the pointers position to be at the start of the array
- we add 2 values to the pointer, which takes it up to element `2`
- now we are setting element `2`'s value to 7
- now we decrement the element which takes us to element `1`
- then finally we assign the element `1` to be 6
- so the arrays state after running this code block is `arr = 1,6,7,4,5`

```txt
Conceptual Question:
Q: Why does p + 1 add 4 bytes (not 1 byte) when p is an integer pointer?
```
- because pointer arithmetic doesnt add bytes individually, but instead adds them as in whole positioning, it scales by data, not individual bytes.
- this is used for incrementing by elements in arrays

```c
int arr[5];
arr = arr + 1;
```
- this code will not work, because even though we can use arrays as pointers, we can not change thier elements. they will always point to the first element
- the only way to change their elements, are to assign them to a different element, and increment/decrement that element
```c
// fixed code
int arr[5];
*p = arr;
p++; // this will incremenet the array by one
```

# Multidimensional Arrays 
```c
int arr[3][4]
```
- this array above creates an array with 3 rows, and 4 columns
- something similiar to this
```txt
arr: [0,0][0,1][0,2][0,3]  <- Row 0
     [1,0][1,1][1,2][1,3]  <- Row 1
     [2,0][2,1][2,2][2,3]  <- Row 2

```
- but memory wise, a 2d array is stored as one continuous memory block
- `Memory: [0,0][0,1][0,2][0,3][1,0][1,1][1,2][1,3][2,0][2,1][2,2][2,3]`
- now accessing a pointer in a sd array is somewhat similiar to how it would be in regular array
```c
int arr[3][4];       // we are initializing an array here, 4x3 
int *p = &arr[0][0]; // now here we are assigning a pointer to the very first element of the array
int (*row_p)[4] = arr; // here we are appointing to the entire row

```
- moving through pointers is the same way it would work in a regular array
```c
// moving through an arrays
p++; // moves from one element to the next

row_p++; //moving from row to the next
```

## What does it mean by larger programs?

- often times C is used to create programs and applications on the larger scale
- adding everything into to the same c file can get annoying, disorganized, and too long
- with that in though, we can create files called header files
- header files are files with the title of a function, and they reduce the amount of code written in the main function
- header files end with the `.h` extension

## Why Create Header Files?

### 1. **Modularity**

- **Separation of Concerns**: Header files allow you to separate function declarations and type definitions from their implementations. This modularity makes your code cleaner and easier to manage.
- **Logical Grouping**: By grouping related functions and types in a header file, you make it easier to understand the structure of your program.

### 2. **Code Reusability**

- **Sharing Function Declarations**: Header files enable you to declare functions that can be used across multiple source files. This means you can write a function once and use it in different parts of your program without rewriting the code.
- **Library Creation**: You can create libraries of functions (e.g., mathematical operations, utility functions) in header files that can be reused in different projects.

### 3. **Easier Collaboration**

- **Team Development**: In larger projects, multiple developers can work on different modules. Header files provide a clear interface for each module, making it easier for team members to understand how to use functions defined in other parts of the codebase.
- **Documentation**: Including comments and documentation in header files helps other developers understand the purpose and usage of functions without delving into the implementation details.

### 4. **Simplified Code Maintenance**

- **Easier Updates**: If a function’s implementation needs to change, you can do so in one place (the source file). As long as the function signature remains the same in the header file, the rest of the codebase remains unaffected.
- **Version Control**: Changes to the header files can be tracked in version control systems, helping you manage updates and changes more effectively.

### 5. **Preventing Redefinitions**

- **Include Guards**: Header files typically use include guards (`#ifndef`, `#define`, `#endif`) to prevent multiple inclusions of the same header file, which can lead to redefinition errors during compilation.

### 6. **Compilation Efficiency**

- **Incremental Compilation**: When using multiple source files, only the files that have changed need to be recompiled. This can save significant time during the build process, especially in larger projects.

## Creating a header file

- lets assume we are creating a function for the Fibonacci sequence, the header file would look something like this

```c
// this file will be called "fib.h"

#ifndef FIB_H 
// checks if the specific identifier exists 
#define FIB_H

int fib(int a);

#endif
```

- and then our main file looks something like this

```c
#include <stdio.h>
#include "fib.h" // we include this header file (or the path of it)

int fib(int a) {
    if (a <= 0) {
        return 0;
    } else if (a == 1) {
        return 1;  // Base case for Fibonacci
    } else {
        return fib(a - 1) + fib(a - 2);  // Recursive case
    }
}

int main() {
    int n = 5;  // Example input
    printf("Fibonacci of %d is %d\n", n, fib(n));
    return 0;
}
```

## What is a makefile?

- a special file used by the make utility to automate the building / compiling process in C/C++ projects
- defines a set of rules and conditioning for when compilation should take place

## Structure for a Makefile

**target**: the file to be generated ( an executable file or an object file [.o/.out])

**dependencies:** the files that the target file depends on 

**recipe:** is the compilation command that compiles the code (the gcc command)

```c
target: dependencies
	gcc "the flags for compilation"

```

## Target

- can be the executable or object files
- this is the file that will be produced / compiled

## Dependencies

- this is the file that is required to create the target file
- is there are changes in the dependencies the recipe is triggered to compile a new target file

## Recipe / GCC Compilation

- the code that is executed to compile the target file
- this is the last process that is executed in a makefile

# Example

`this solution is from the practice midterm`

```makefile
prog: prog.o
    gcc -Wall -std=c99 prog.o -o prog

prog.o: prog.c common.h
    gcc -Wall -std=c99 -c prog.c

clean:
    rm -f *.o prog
```

**prog**

- the prog function is the first function that is in the makefile
- this function can and will only be executed if `prog.o` exists or is changed
- this function creates a prog file

**prog.o**

- the prog.o function creates an object file
- this function requires `prog.c` and `common.h` to be present to trigger
- change in any of the dependencies triggers the gcc command

**clean**

- clean required no dependencies, but is just an argument
- if its passed as an arg, then it will just clean

## Execution Order

1. Check the target dependencies
2. Rebuild any outdated dependencies first
3. Execute the command to create the target

# Practice Midterm Question

You are given the following Makefile. In each sub-question, you are given a series of commands that are run on the terminal that always include an invocation of make. For each sub-question, show the command(s) from the corresponding targets in the Makefile that will get executed, in the exact order they will be executed in. Note that the commands in (a) are executed first, followed by those in (b), followed by those in (c), followed by those in (d). For (a), assume the directory initially includes only .c and .h files and this Makefile.

```makefile
prog: prog.o
	gcc -Wall -std=c99 prog.o -o prog
	
prog.o: prog.c common.h
	gcc -Wall -std=c99 -c prog.c
	
clean:
	rm -f *.o core
```

### Processes

1. make
    - in the initial make function, since we only start with the `.c` and the `.h` files, and we dont have the `.o` files just yet. the first function that will execute it  `gcc -Wall -std=c99 -c prog.c`
    - after that we will have  produced a `.o` file for the function prog to receive as a dependency so then it will trigger `gcc -Wall -std=c99 prog.o -o prog`
    - after the first execute we will have files `common.h` `prog,c` `prog.o` `prog`
2. touch common.h + make
    - when `touch` a file, it will think it changed because of the timestamp change, so the make file will recompile the functions where `common.h` is listed as a dependency
    - so the first function it will trigger is `gcc -Wall -std=c99 -c prog.c`
    - this will cause prog.o to be recompiled so it will also trigger prog to be compiled `gcc -Wall -std=c99 prog.o -o prog`
    - after the second execute, we will have `common.h` `prog,c` `prog.o` `prog`
3. touch prog.c + make
    - again, when we touch a file, it classifies it as modified. and this triggers the prog.o function to trigger because its dependency is changed
    - so it run `gcc -Wall -std=c99 -c prog.c`
    - and then it also changes the dependency for prog
    - so it runs `gcc -Wall -std=c99 prog.o -o prog`
    - after the execution we will have `common.h` `prog,c` `prog.o` `prog`
4. make prog.o
- since there have been no dependency change from the last compilation, no effect will take place
1. make clean + make prog
- the clean function will remove the `.o` file,  but then the make prog will rebuild the `prog.o` file because it is a dependency for prog
- after execution we have `common.h` `prog,c` `prog.o` `prog`
1. make clean + make prog
- the clean function will remove the `.o` file,  but then the make prog will rebuild the `prog.o` file because it is a dependency for prog
- after execution we have `common.h` `prog,c` `prog.o` `prog`

### Result

we are left with 

- `common.h`
- `prog.c`
- `prog.o`
- `prog`
- `makefile`

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
## What is Recursion?

- 	Definition: Recursion is a method of solving a problem by breaking it down into smaller, self-contained subproblems.
- 	Approach:
- 	Base Case: If the problem is simple enough, solve it directly.
- 	Recursive Case: If not, reduce it to simpler instances of the same problem.

## Recursive Functions

- 	Definition: A function that calls itself to solve subproblems.
- 	Structure:
- 	Termination Condition: Ensures that the recursion eventually stops (base case).
- 	Recursive Call: Calls the same function with a smaller input to progress towards the termination condition.

### Example 1: Factorial
```C
int factorial(int n) {
    if (n <= 1)
        return 1;
    return n * factorial(n - 1);
}
```
## Example 2: Fibonacci Numbers

- 	Sequence: 0, 1, 1, 2, 3, 5, 8, 13, …
- 	Formula:  F_n = F_{n-1} + F_{n-2} 
- 	Base Cases:  F_0 = 0 ,  F_1 = 1 

```c
int fib(int n) {
    if (n <= 1)
        return n;
    return fib(n - 1) + fib(n - 2);
}
```
## what are strings in C?

- C doesnt have a built in type for strings, instead, strings are actually just arrays of char types

```c
	// these are all strings, but they are using the array data type

char str1[] = "Hello World"; 
// we are creating an array with an indefinite amount of elements, and adding strings inside it
char str2[11] = "Hello World";
// we are creating an array with 11 spaces inside it, and we are assinging hello world to it
char *str3 = "Hello World";
// here we have a pointer to a assumed premade array called str3, since the pointer starts at the start of the array, so from the start we are adding "hello world" to the array

```

- so then what is happening in the memory?

```
In memory:
str1: ['H']['e']['l']['l']['o']['\0']
                                 ^
                                 This is the null terminator!, it tells the compiler, when the string has ended
```

## The difference between string literals and string variables

`Summary of the differences`

- literals aren't mutable while variables are
- literals are stored in read only memory, while variables are stored in read-write memory

**In a string literal**

- is a fixed sequence of chars, enclosed in double quotes
- when you write a string literal it is in read only memory, it is ***IMMUTABLE***
- since the variable is not an array, we cannot modify it at runtime, what ever is assigned to it, is what we get the result as

```c
char *str = "Hello World";
// the pointer is pointing to the string literal
// hello world, 
```

**in a string variable**

- a string variable is a bunch of chars appended to an array, and since its in an array it is ***MUTABLE***
- when you declare a a char and initialize it, it is stored in writable memory

```c
char str[] = "Hello World";
// we created an array and we added the chars 
// "hello world"
// this is what it looks like raw Hello World\0
```

## The Null Terminator

- the null terminator is very important to strings in C

```c
char str[4] = "Home"
/* having this alone is bad
* every string in C needs to have a null terminator
* "\0" - the null terminator tells the compiler when the string stops
since we only have enough space for the text, we dont have space in memory for the null operator, we will pprobably get a segmentation fault*/
```

- to visualize this is what it looks like

```
What we want:    ['H']['o']['m']['e']['\0']  // Needs 5 bytes!
What we get:     ['H']['o']['m']['e']        // No room for '\0'!
```

## Writing string using Scanf

- while reading and writing string from scan f isnt very complicated, here are something to watch out for
- lets say we need to create a program that will take in a scanf input and print the name taken.

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
	char name[50];
	
	scanf(&s, name);
	printf("%s", name);
	return 0;
	}
	
	/* there is a crucial problem with this code
	* if there is a case where the name entered is >50
	* then there could be overflow and seg fault
	* but if we assign the scanf to only accept 49 char
	we can reduce the chances of running into errors*/

#include <stdio.h>
#include <stdlib.h>

int main(void) {
	char name[50];
	
	scanf(&49s, name);
	printf("%s", name);
	return 0;
	}
```

## The String Library

- C provides several essential libs, and one of them happens to be a library for string manipulation

```c
#include <string.h>

char str1[50] = "Hello";
char str2[50];

strlen(str1);         // Returns 5 (doesn't count '\0')
strcpy(str2, str1);   // Copies str1 into str2
strcat(str2, " World"); // Adds " World" to end of str2
strcmp(str1, str2);   // Compares strings (-1, 0, or 1)
```

## Practice Questions

### Question #1

- Why does `char *p = "hello";` store an immutable string, but `char arr[] = "hello";` allows for modification of the chars in arr?
- `Solution`: this is the difference between string literals and string variables. since string literals are stored in read only memory, they are immutable. string variable in essence are just arrays with chars inside of them. since arrays are stored in write memory, they are mutable, so we can modify them

### Question #2

- What happens when you try to assign a character to `*p` in the example `char *p = "hello";`? Why?
- `Solution`: it just points to the memory address of the string literal, its in ready only so you cant do anything with is

### Question #3

- Given a character array `char str[10] = "abcde";`, what happens if you mistakenly overwrite the `'\0'` at the end of the string?
- `Soltution`: You will encounter a segmentation fault, because there it not any space for there to be a termination operator

### Question #4

- Define a character array `char str[] = "Hello World";`. Write a C program snippet to print each character one by one until the end of the string.
- `Solution`

```c
#include <stdio.h>

int main(void) {
	char str[] = "Hello World";
	int i = 0;
	
	while (str[i] !='\0') {
	 printf("%c",str[i]);
	 i++
	}
	return 0;
}
```

`typedef` = create alias for an existing type

# Structs

## what are Structures?

- well structures, also known as structs is a data structure where multiple variables of different types can be stored
- think of it as a dictionary from python
- they are declared using the `struct` keyword
- unlike arrays, the members of a struct can all be different types

```c
struct Person {
	int age;
	char name[20];
	char sex;
} person1;

```

now that we have created a struct we have to initialize it, and this can be done like so

```c
struct Person person1 = {23,"Bob","M"}
	// with this, we have passed thruough the appropriate values according to the struct
```

sort of like dictionaries in python, each struct can have different scopes with different values, adding nested structs can aid with it

```c
struct Student {
	struct Person name;
	int id;
} student1;
```

# Unions

## What are Unions?

- they are similar to structs, but they save memory
- all members in a union share the same memory space, so only one member can hold a value at a time

### Use Cases

- unions are often used to store variables of different types, but where only one value is required at a time, they are also common in creating compact data structures

```c
typedef struct {
	int kind; // 0 for an int, and 1 for a double
	union {
		int i;
		double d;
	} value;
} number;
```

# Enumerations

## What are Enumerations

- define a set of named int constants, which makes code more readable
- using smaller sets of possible values

```c
	typedef enum { CLUB, DIAMOND, HEART, SPADE } Suit;
	Suit card = HEART;
```

- to the compiler, they are treated as regular int’s, and you can specify a value needed