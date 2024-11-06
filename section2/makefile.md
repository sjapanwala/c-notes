## What is a makefile?

- a special file used by the make utility to automate the building / compiling process in C/C++ projects
- defines a set of rules and conditioning for when compilation should take place

## Structure for a Makefile

**target**: the file to be generated ( an executable file or an object file [.o/.out])

**dependencies:** the files that the target file depends on 

**recipe:** is the compilation command that compiles the code (the gcc command)

```c
target: dependencies
	gcc "the flags for compilation"

```

## Target

- can be the executable or object files
- this is the file that will be produced / compiled

## Dependencies

- this is the file that is required to create the target file
- is there are changes in the dependencies the recipe is triggered to compile a new target file

## Recipe / GCC Compilation

- the code that is executed to compile the target file
- this is the last process that is executed in a makefile

# Example

`this solution is from the practice midterm`

```makefile
prog: prog.o
    gcc -Wall -std=c99 prog.o -o prog

prog.o: prog.c common.h
    gcc -Wall -std=c99 -c prog.c

clean:
    rm -f *.o prog
```

**prog**

- the prog function is the first function that is in the makefile
- this function can and will only be executed if `prog.o` exists or is changed
- this function creates a prog file

**prog.o**

- the prog.o function creates an object file
- this function requires `prog.c` and `common.h` to be present to trigger
- change in any of the dependencies triggers the gcc command

**clean**

- clean required no dependencies, but is just an argument
- if its passed as an arg, then it will just clean

## Execution Order

1. Check the target dependencies
2. Rebuild any outdated dependencies first
3. Execute the command to create the target

# Practice Midterm Question

You are given the following Makefile. In each sub-question, you are given a series of commands that are run on the terminal that always include an invocation of make. For each sub-question, show the command(s) from the corresponding targets in the Makefile that will get executed, in the exact order they will be executed in. Note that the commands in (a) are executed first, followed by those in (b), followed by those in (c), followed by those in (d). For (a), assume the directory initially includes only .c and .h files and this Makefile.

```makefile
prog: prog.o
	gcc -Wall -std=c99 prog.o -o prog
	
prog.o: prog.c common.h
	gcc -Wall -std=c99 -c prog.c
	
clean:
	rm -f *.o core
```

### Processes

1. make
    - in the initial make function, since we only start with the `.c` and the `.h` files, and we dont have the `.o` files just yet. the first function that will execute it  `gcc -Wall -std=c99 -c prog.c`
    - after that we will have  produced a `.o` file for the function prog to receive as a dependency so then it will trigger `gcc -Wall -std=c99 prog.o -o prog`
    - after the first execute we will have files `common.h` `prog,c` `prog.o` `prog`
2. touch common.h + make
    - when `touch` a file, it will think it changed because of the timestamp change, so the make file will recompile the functions where `common.h` is listed as a dependency
    - so the first function it will trigger is `gcc -Wall -std=c99 -c prog.c`
    - this will cause prog.o to be recompiled so it will also trigger prog to be compiled `gcc -Wall -std=c99 prog.o -o prog`
    - after the second execute, we will have `common.h` `prog,c` `prog.o` `prog`
3. touch prog.c + make
    - again, when we touch a file, it classifies it as modified. and this triggers the prog.o function to trigger because its dependency is changed
    - so it run `gcc -Wall -std=c99 -c prog.c`
    - and then it also changes the dependency for prog
    - so it runs `gcc -Wall -std=c99 prog.o -o prog`
    - after the execution we will have `common.h` `prog,c` `prog.o` `prog`
4. make prog.o
- since there have been no dependency change from the last compilation, no effect will take place
1. make clean + make prog
- the clean function will remove the `.o` file,  but then the make prog will rebuild the `prog.o` file because it is a dependency for prog
- after execution we have `common.h` `prog,c` `prog.o` `prog`
1. make clean + make prog
- the clean function will remove the `.o` file,  but then the make prog will rebuild the `prog.o` file because it is a dependency for prog
- after execution we have `common.h` `prog,c` `prog.o` `prog`

### Result

we are left with 

- `common.h`
- `prog.c`
- `prog.o`
- `prog`
- `makefile`