# Functions

- are used to divide programs
- avoid duplications

## Body of a Function

```c
return-type function-name ( parameters ) {
		declerations
			statements
}
```

### Starting of a Function (return-type)

- CANNOT BE AN ARRAY
- when defining a function, you have to specify what type of value will be returned. an example is main, main return a code which signifies if the execution was successful or not (code 0 or >0 ). since it returns an int, we start the function with

```c
int main(void) { // int to specify 
	// add code here
	return 0;
}
```

### Function Name

- a function name is just a way to call a function
- cannot be a reserved type

### Parameters

- are separated by a comma, and must have a type
- the parameter list needs to be enclosed by parenthesis (…)
- if there are no parameters, we use void

```c
char name(void) { // we use void, because we arent taking any params
	if (1+1) == 2 {
		return "Hello World"
	}
}

int value(int argc, char* argv[]) { // we are using arguementas params
	return 5
}
```

### Calculating the Average

- instead of copying and pasting code, we use functions to repeat the same functions

```c
double average(double a, double b) {
	return (a+b) / 2;
}
```
