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

## How Does `Printf` Work?

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

### Some **Padding** 

```txt
- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
TL;DR
Form: %m.pX or %-m.pX
‣ m is an optional integer constant that specifies the
minimum field width

‣- is used to specify left justification of the output text

‣ p is an optional integer constant that indicates precision; if
omitted, so is the period

‣ X is the required placeholder that specifies the type

- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 
```
the `printf` function has a few parameters that can be used to pad the output to a certain number of characters, to ensure the correct amount of digits is displayed

- for example, we can use `%5d` to pad the output to 5 spaces before displaying the int
    - `%5d` will create the variable to be 5 characters long, so if the variable is 3 chars long, it will create 2 spaces before the variable
    - we can add a zero before the 'five' in this case, to replace the spaces with zero's


```c
#include <stdio.h>

int main() {
    int a = 42;
    printf("The variable a is %5d\n", a);
    return 0;
}
/* the output will be similiar to this...
* (the "_" represent a single space)
* > ___42
*/
```

We can do the same with floats, but we need to change the placeholder 

- for example, we can use `%5f` to pad the output to 5 spaces before displaying the float or we can add a period before the number, to pad 5 places after the decimal point in the float
    - if we have a float of 42.24, the output of %5f will be 42.24, since it controls the entire number; sets the width of 5 digits (decimal counts as a digit)
    - **BUT** if we add a period before the number, then that number will control how many places the decimal is printed
    - if we combine the two, sort of like `%5.2f` this will allow us to control both. so the actual lenght of the entire number including the decimals will be 5 and there will only be 2 decimal places

```c
#include <stdio.h>

int main() {
    float a = 42.24;
    printf("The variable a is %10.2f\n", a);
    return 0;
}

/* the output will be similiar to this...
* (the "_" represent a single space)
* > _____42.24
*/
```

### Escape Characters

esacape codes allow you to manipulte the formatting of your string without altering the text, some common escape codes are,

| Escape Code | Name | Description  |
| :---: | :---: | :---: |
| \" | Double quote | Prints a double quote without ending the string |
| \b | Backspace | Prints a backspace character, deleting the last character in the string |
| \n | Newline | Prints a newline character, moving the cursor to the next line |
| \\ | Backslash | Prints a backslash character, as they are normally used for escape codes |
| %% | Percent | Prints a percent character, when they are normally used for formatting |
| \t | Tab | Prints a tab character, moving the cursor to the next tab (~8 spaces) |
| \a | Alert | Sounds an alert bell |
| \r | Carriage Return | Moves the cursor to the beginning of the line |

## Hoow Does `Scanf` Work?

`scanf` is the opposite of `printf`, it reads input from the console and stores it into a variable, to use `scanf` we have to follow a guideline

`scanf("string %place_holder\n", &variable_name);`
