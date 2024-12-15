# Welome to Variables in C
variables are used to store data values. in c, variables need to be defined a type before we can allocate data into them.

the different data types in c area:
```c
int 
//  an int is a whole number, it can be positive or negative. we also use ints to store arrays
float 
// a float is a decimal number, so 1 is not a float, while 1.0 is.
double 
// a double is a float with more precision, it is used for storing decimal numbers with higher accuracy. double precision floating point number
char 
// char is the data type that stores characters, to store strings, it makes more sense to add them to an array (will be covered in section 2). 
_Bool 
// bool is a data type that is used with the help of a library (c99), its not natively supported in C. ways to vatively support boolean values in c is by making them equal 0 or 1, where its false and true respectively.
```
## What each variable is and what it does

| Data type | Description | Example | Memory Size |
| --- | --- | --- | --- |
| int | a whole number (can be positive or negative) | 1 | 4 bytes |
| float | a decimal number to a single precision | 1.0 | 4 bytes |
| double | a decimal number that is double precision | 1.0 | 8 bytes |
| char | a character | 'a' | 1 byte |
| _Bool | a boolean value | true | 1 byte |
| void | is techinally a data type, but holds no value | void | 0 bytes |

**Whats with there being two floating point values?**

- A float, which is to a single precision
    - a float stores about 6-7 decimal places
    - in a scenario where we need to store very small numbers, we would not use a float because after around 7 decimal places, they start to loose thier precision
- A double, which to to double precision
    - a double stores about 15-16 decimal places
    - in a scenario where we need to store very small numbers, we would not use a double because after around 16 decimal places, they start to loose thier precision

## Defining variables

as mentioned before, do define a variable we need we need to define a datatype first, from one of the data types listed above.

```c
int x;
/*
* we can see that we have defined an intiger called `x`, 
*but currently this variable doesnt hold any values or data.
*/
```

```c
int x = 1;
// now we have added a vlue of 1 to out variable x
```


```c
int x = 1;
int y = 2;
int z = x + y;

// using the values defined, we can add them together and store them in a new variable called z, which is the sum of both x and y
```


