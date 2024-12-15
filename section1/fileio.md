# File I/O

in C, interacting with the terminal can provide us with input and output. This is done using the `printf` and `scanf` functions that are provided in the `STDIO.H` library

## Understanding Place Holders
in C when we run a `printf` or a `scanf` function, place holders are very importants since they dictate what type of data the being printed / read from the console

some place holders include:

| Place Holder | Type of Data | Usage |
| :---: | :---: | :---: |
| %d or %i | Integer | Signed intigers (42, -42, etc...) |
| %u | Unsigned Integer | Unsigned intigers (**ARE NOT LIKE SIGNED, THEY CAN ONLY CONTAIN POSITIVE NUMBERS) |
| %f | Float | Floating point numbers (42.42, -42.42, etc...), single precision |
| %lf | Double | Floating point numbers (42.42, -42.42, etc...), double precision |
| %c | Character | Single character ("A") |
| %s | String | String of characters (char a[] = "Hello World"; ) |
| %e | Scientific Notation | Floating point numbers (42.42e3, -42.42e3, etc...) |

## How Does Printf Work?

to use printf, we need to include the `stdio.h` library, and follow a set guideline on how it works

`printf("string %place_holder\n", variable_name);`

following this format ensures that the printf function will print the variable_name in the place_holder location in the string

```c
// an example on how to printf "Hello World!"
#include <stdio.h>

int main() {
    printf("Hello World!\n");
    return 0;
}

// now how to print a variable using a place holder
#include <stdio.h>

int main() {
    int a = 42;
    printf("The variable a is %d\n", a);
}
```
