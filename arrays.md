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
