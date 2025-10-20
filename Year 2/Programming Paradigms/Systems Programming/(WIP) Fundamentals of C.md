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
# Comparison

Originally, C did not have a boolean type and only used int. Therefore, it used 0 as false and 1 as true. C99 does have `bool` but most standard library functions still use the integers as convention
# Statements and Compound Statements

A statement is a single instruction terminated with a semicolon, like:

```
printf("Hello world!\n");
```

A **compound statement** is a set of statements surrounded by curly brackets:

```
{
printf("Hello ");
printf("world!\n");
}
```
# Iteration Statements
## While

```
while (expression) {
	statement
}
```
## Do

```
do {
	statement
} while (expression);
```
## For

```
for (expr1 ; expr2 ; expr3) {
	statement
};
```

Our expressions are (in order) our initialisation, conditional and increment
## Break

This statement causes the innermost enclosing loop to be exited immediately
## Continue

Causes the next iteration for the loop to begin
## Switch

```
switch(expression) {
	case const-expr: statements
	case const-expr: statements
	default: statements
}
```
# Variables

Variables and constants are basic data objects manipulated by a program

Declarations declare the variable used, their type and possibly initial value. An expression combines variables and constants to form new values
## Data Types

Every C variable must have a type, here are the common ones:

- `char`: a single byte, often used for a character
- `short`: an integer type, representing small whole numbers
- `int`: an integer type, representing whole numbers
- `long int`, `long long int`: an integer type, representing large or very large whole numbers
- `float`: a single precision floating point number
- `double`, `long double`: double precision floating point number
## String

String constants are zero or more characters in double quotes. A string n array of chars that has a `NULL` character at the end of the string `\0` 
# Enumeration

Allows us to declare our own type with a list of acceptable values like `enum suit{CLUBS, DIAMONDS, HEARTS, SPADES};`
# Functions

Functions encapsulate code, similar to methods in an object-oriented language. They are declared like so:

```
return-type function-name ( parameters ) {
	code
}
```