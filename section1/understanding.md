LECTURE: SEPT 9, 11, 13

## Solve This Question!

- Want to create a program that calculates the weight of a box
- `volume = lenght * width * height`
- With a global variable of inches per pound of 166
- Require 5 Variables
    - Height
    - Length
    - Width
    - Volume
    - Weight

```c
#include <stdio.h>
#define INCHES_PER_POUND 166 //here we are defining a global var//

int main(void) {
	int height = 8;
	int lenght = 12;
	int width = 10;
	
	int volume = height * lenght * width;
	int weight = (volume + 165) / INCHES_PER_POUND
	printf("Dimensions: %d * %d * %d\n", lenght, width, height);
  printf("Volume (Cubic Inches): %d\n",volume);
  printf("Dimensional Weight (pounds): %d\n",weight);
  return 0;
}
```

```
The Output Of The Function Above When Compiled With
gcc -Wall -Werror -std=c99 <filename.c> -o <outputname>

~/CMPUT_201/notes › ./<filename.c>
Dimensions: 12 * 10 * 8
Volume (Cubic Inches): 960
Dimensional Weight (pounds): 6
```

### How `scanf` works

- works sequentially, so it will read in order
- if an inappropriate char is encountered
    - it will stop processing

```c
int main(void) {
	int a, b, c;
	scanf("%d%d%d", &a &b, &c);
	return 0;
	}
	
/*
Input: 5,2,3
Output: 5,2,3

Input: 1,2,3,4
Output 1,2,3 -> since there are only 3 vars
```

### What is `&` ?

- &x is the memory address of variable x
- Basically, scanf converts input characters
(those entered in terminal) and converts them to
internal form of data (binary representation) to
be able to store them in memory
- anything that isn't used thats in the memory, is called garbage memory

# Expressions

### Arithmetic Operators: (+, -, *, /, %)

- Unary Plus `+` (right assoc)
- Unary Minus `+`  (right assoc)
- Binary Plus `+` (left assoc)
- Binary Minus `-` (left assoc)
- Multiplication `*`
- Division `/`
- Remainder / Mod `%`

### Relational Operators: (>, <, >=, <=,==)

### Logical Operator: (!, &&, ||)

## Assignment Operators: (=, +=, -=, *=, …)

- a simple assignment operator `=`
- compound operators:
    - `+=` , `-=`
- no rounding ‘cuts off a decimal’

```c
int i;
float f;
i = 72.99f; /* i is now 72 */
f = 136; /* f is now 136.0 */

// what ever is after the = has to conform with the type//
```

### Side Effects

- modify the operand
- the side effect is the number gets assigned to the variable
- the main effect is returning the value

```c
i = j = k = 0; //equivalent to i = (j = (k =
0));
i += j += k; //equivalent to i += (j += k);
```

### Requiring an L Value

- L Value, Left Value = an object that is stored in computer memory

### Increment and Decrement Operators

- increment operator: `++`
- decrement operator: `--`

‣ postfix: i++; // (use the value of i then) increment it

- In **postfix notation**, the operator is placed **after** the variable. The value of the variable is used **first** in the expression, and then it is incremented or decremented.
- highest precidence

```c
int x = 5;
int y = x++;  // Postfix increment
/*
Here’s what happens:

	1.	The value of x (which is 5) is assigned to y.
	2.	x is then incremented to 6.
	
	After this, x = 6 and y = 5.
/*
```

‣ prefix: --i; //decrement i (and then use its value)

- In **prefix notation**, the operator is placed **before** the variable. The variable is incremented or decremented **before** its value is used in the expression.
    
    ```c
    int x = 5;
    int y = ++x;  // Prefix increment
    
    /*
    Here’s what happens:
    
    	1.	x is incremented to 6.
    	2.	The value 6 is then assigned to y.
    	
    	After this, x = 6 and y = 6.
    */
    ```
    

```c
int i = 1, j = 2, k;
k = i++; //k = 1, i =2
k = --j; //j = 1, k=1
k - i + 1;
```

## Expression Statements

++i; // is a statement, but the result of this
expression is discarded since no one used it

i++; // is a statement. The value of i is
fetched but not used. However, the value of i
is actually incremented after executing this
statement. i.e., there is a side effect

i * j - 1; // the result of this expression is
computed and discarded

`gcc -Wall -std=c99 -ggdb <filename> -o <filenameout>`