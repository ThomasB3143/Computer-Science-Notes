#wip Section: [[Systems Programming (Root)]]
C provides low-level access to memory with efficiency and flexibility
# Compiling with GCC

`gcc -o outfile file.c`

- `-o` to name the output
- `-E` does pre-processing only
- `-S` goes as far as compilation only
- `-c` goes as far as assembly only
# Pre-processing

Lines that start with "#" are commands to the C pre-processor, a piece of software that can edit C programs prior to compilation
## include

Includes the specified file before compilation, use <> for system files and "" for files in the current working directory
## define

Used to provide definition in code like so:

```C
#define PI 3.14
```

You can specify name and values at compile time like this:

`gcc -DPI=3.14 myProgram.c`

You can use `#ifdef A_NAME` or `ifndef A_NAME` to check if a variable has been defined for conditionals
# Functions

## Entry Function

All C programs have the "main()" function, called at runtime to start the program
## Returning

The return value for a function must be of the type specified in the header, for example:

```C
int doubleNumber(int num){
	return num * 2;
}
```
# printf()

Implements formatted text printing to the console. The first parameter explains how the rest are formatted through the following rules:

- `%d` signed decimal (int)
- `%u` unsigned decimal
- `%o`,`%x` octal, hexadecimal
- `%l` long
- `%f` floating point such that `%1.2f` will give `3.14`
- `%e` floating point in exponent form
- `%c`,`%s` character, string

Here is a great example:

```
double F = 10;
double C = ((F-32) * 5) / 9;
printf(" %2.3f F = %f C \n", F, C)l
```

This will print `10.000 F = -12.22222 C`
