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