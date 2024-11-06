## Boolean Values in C

- There is no built-in “bool” or “boolean” type in C. Basically 0 is false and
any non-zero value is true.
- In C99, there is a type _Bool, which is basically an integer type with
values 0 (false) or 1 (true)

### The If Statement

- Form

```c
if ( expression ) statement or
if ( expression ) {statements} — a sequence of 
multiple statements
enclosed in curly brackets is called a compound statement

/*
 Required use of parentheses to enclose the expression
 When “true” (i.e., expression is non-zero), the statement(s) is/are executed */
```

### Operators

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/c4a2e626-a81f-422b-b640-6fda28cf38bf/86085994-5365-4d20-bfc8-056931da8ecb/image.png)

### Short Circuit Evaluation

```c
int i = 10;
int j = 2;
if ((i == 10) || (j == 5)) {
	printf("Hello World");
}

/* english,
	read evaluations from left to right, if the   first expression is true, we dont need to keep going, if theres no need we dont keep going */
	
int i = 10;;
int j = 2;
if ((i != 10) && (j < 5)) {
	printf("Hello World")
} 

/* english
since the first condition is false, we would stop there, but if the first condition is satisfied, we go to the next one. if the next condition is satisfied, then the if statement can occur, else it wont. */

```

---

## Loops

- loops in C are similar to how they are in Python… but very different.

### `While` Loop

- while loops have an action statement, followed by a controlling expression.
- usually when a value is from a bool, or when a number is less than or greater.

```c
//Basic While Loop

int n = 5;        // inits n as 5
int i = 0;        // inits i as 0
while (i < n) {   // while i is less than 5
	printf("Attempts Completed: %d", i);
	i++;            // increments i by one, so its not an inf loop
} 

// will print "Attempts Completed: 0...4"
```

### `Do` Loops

- do statements have a statement followed with a while and then a controlling statement.
- kind of a reverse while loop, it will execute the do statement, as long as the while statement is true

```c
// Basic Do Loop

int i = 0;
int n = 5;
do {
	printf("Hello World");
	i++;
} while (i < 5);

// Will print "Hello World" 5 Times
```

### `For` Loops

- takes a couple of expressions and then evaluates an statement until the expressions have been satisfied
- Expression 1 → is usually the initialization of the variable `int i = 0;`
- Expression 2 → is usually the controlling loop `i < n;`
- Expression 3 → is usually the incrementing expression `i++`

```c
// Basic For Loop

int n = 5;
for (int i = 0; i < n; i++) {
printf("Hello World");
}

// Will print "Hello World" 5 Times
```

## Other Loop Statements

- `Break;`
    - the break statements exits from a loop from the middle of a statement
    - breaks out of the innermost loop
- `Goto;`
    - goes to the identifier that its labeled with
    - is not recommended to use by *Big Daddy Djikstra*
- `Continue;`
    - the continue statement does not completely exit the loop, the ends the current iteration
    - only use inside loops
- `Null;`
    - is an empty statement that only contains semi-colons