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