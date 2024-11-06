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