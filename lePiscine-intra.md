# PISCINE C - C LANGAGE
## C in 42 min

```c

```
# PISCINE C - DAY 00
## Basic commands

```c

```
## Filesystem

```c

```
## touch, cat

```c

```
# PISCINE C - DAY 01
## echo, cat, more

```c

```
## head, tail, grep

```c

```
## Redirections

```c

```
## sort, cut

```c

```
## wc, ifconfig, bc, find, env, export

```c

```
## stdout, stderr

```c

```
# PISCINE C - DAY 02
## First step in C

```c

```
```c
void ft_putchar(char c, int n);
```
# PISCINE C - DAY 03
## Introduction to pointers

```c

```
Pointers
variable type. allows to process another variable's address

32b -> 4GB
64b -> 2^64

MMU
allows to reserve memory somewhere, physically on the computer

MEMORY
divided in two parts
high memory -- stack -- used every time time a function is called --top-down
low memory -- heap -- place where you can allocate memory --bottom-up

## Assignment

```c

```
```c
void		ft_putchar(char ptr);
void		ft_putnbr(int ptr);
void		ft_putaddr(void *ptr);


int	main()
{
	int	a;
	int	*ptr;

	a = 3;
	ptr = &a; /* retrieves a's address*/
	ft_putaddr(ptr);
	a = 42;
	ptr = &a; /* retrieves a's address*/
	ft_putaddr(ptr); /* same result (address) is shown*/
	return(0);
}

--incompatible type issue
```
## Dereferencing

```c
int	main(void)
{
	int	a;
	int	*ptr;
	int **ptr2; /* <-- 4º momento */

	/* 1º momento */
	a = 3;
	ptr = &a;
	ptr2 = &ptr; /* 4º momento */
	ft_putnbr(*ptr);
	/*4º momento */
	ft_putnbr(**ptr);
	/* 2º momento */
	a = 42;
	ft_putchar('\n');
	ft_putnbr(*ptr);
	/* 2º momento */
	*ptr = 42;
	ft_putchar('\n');
	ft_putnbr(a);
	return(0);
}
```

## Pointer arithmetic

```c
int	a;
int	b;

a = 3;
b = 42;
ft_putaddr(&a);
ft_putchar(' ');
ft_putaddr(a);
ft_putchar('\n');
ft_putaddr(&b);
ft_putchar(' ');
ft_putaddr(b);
ft_putchar('\n');
return (0);

```
## Arrays

```c
/* Exemplo 1 */
int	tab[10];

tab[0] = 42; /*Equivalentes*/
*(tab + 0) = 42; /*Equivalentes*/
ft_putaddr(tab); /*imprimiu o endereço*/
ft_putchar(' ');
ft_putnbr(tab[0]); /*imprimiu 42 (primeiro elemento)*/
ft_putchar('\n');
return(0);

/*Exemplo 2*/
int	tab[10];
int	*ptr;

ptr = tab;
*(ptr + 3) = 867 /* (ptr + 3) é um endereço, *(ptr + 3) é um int */
tab[0] = 42;
ft_putaddr(tab); /*imprimiu o endereço*/
ft_putchar(' ');
ft_putnbr(tab[3]); /* imprimiu o conteúdo = 867*/
ft_putchar('\n');
return(0);

/* Exemplo 3 */ /* Equivale */
tab[0] = 42;
*(tab + 10) = 42; /* Equivale*/

/* Exemplo 4 */

int	tab[10];
int	tab2[10];
int	*tabptr2;
/* 4 octets */

/* Exemplo 5 */
int	tab[10];
int	*ptr;

ptr = tab;
*(ptr + 3) = 867;

/* Exemplo 6 */ 
int	tab[10];
int	tab2[10];
int	*tabptr[2];
tabptr[0] = tab;
tabptr[1] = tab2;
tabptr[1][3] = 42; /* Equivale */
*(tabptr[1] +3)) = 42; /* Equivale */
*(*(tabptr +1) +3) = 42; /* Equivale */


```
## Character string

```c
char		*ptr;

ptr = "toto";
ft_putchar(*ptr); /* Equivale */
ft_putchar(ptr[0]); /* Equivale */
ft_putchar('\n');
return(0);

/* Exemplo 2 */

char *ptr;
char *ptr2;


```
## Pointer usage

```c
void	ft_putchar(char ptr);
void	ft_putnbr(int ptr);
void	ft_putaddr(void *ptr);

void	fct(int *a)
{
	*a = 30 + *a;
}

int	main(void)
{
	int a;

	a = 42;
	fct(&a);
	ft_putnbr(a);
	ft_putchar('\n');
	return (0);

}

```
## void *

```c
void 	ft_putchar(char ptr);
void 	ft_putnbr(int ptr);
void 	ft_putaddr(void *ptr);

int 		main(void)
{
	int 	a;
	int 	*ptr;
	int 	**ptr2;
	void	*superptr;

	a = 3;
	ptr = &a;
	ptr2 = &ptr;
	superptr = &ptr2;
	ptr = superptr;
	superptr[1] = 12;
	// or:
	*(superptr + 1) = 12;
	return(0);
}
```
# PISCINE C - DAY 04
## Introduction
Theory + Practice;
how to call a function;
how to pass it parameters;
how to make it return values;
how it's evaluated.

## Recursion - Theory
Recursivité - Théorie

itérative
e.g. ft_strlen

programmation récursive est un peu différent

sont les fonctions qui vont a'appeler elles mêmes et se rappeler elles même, se rappeler elles même, se rappeler elles même...

matroska

la pile

la stack

zone de memoire

ft_strlen iterative vs recursive

factorielle
`5! = 5 * 4 * 3 * 2 * 1`

programming method;

iterative programmation;

recursive prog.

stack: fills up as we call functions;

everytime we call a function, this function will be pushed onto the stack, it'll evaluate itself, and, at some point, when we are done with our function, we'll return to previous function
functions pile up one on top of another

a recursive function is a function that calls itself and pushes itself on the stack, on top of itself.

2 possible outcomes:
1. overflow of the stack
2. condition that states whether a criteria is met, then we can stop calling it.

## Recursion - Practice
Recursivité - Pratique
```c
#include <unistd.h>

int 	fn(int i)
{
    if (i <= 5)
    {
        i += 1;
        write(1, "D", 1);
        fn(i);
        write(1, "F", 1);
        return(0);
    }
	else
    {
        return (0);
    }
}

int 	main()
{
    fn();
    return (0);
}
```

# PISCINE C - DAY 05
## Char string manipulation

```c
void	ft_putchar(char c)
{
    write(1, &c, 1);
}
void	ft_putstr(char *str)
{
    int 	index;
    index = 0;    
    while (str[index] != '\0')
    {
        ft_putchar(str[index]);
        index++;
    }
}
void	replace_first_h_with_y(char *str)
{
    str[0] = 'y';
}
void	replace_first_char(char *src, char *dest)
{
    dest[0] = src[0];
}
int 	main(void)
{
    char 	str1[] = "Hello";
    char	str2[] = "Yello";
    replace_first_h_with_y(str1);
    ft_putchar('\n');
    replace_first_char(str1, str2);
    ft_putstr(str1);
    ft_putchar('\n');
    ft_putstr(str2);
    ft_putchar('\n');
    return (0);
}
```
# PISCINE C - DAY 06
## Introduction
Libraries
- what are those used for
- how to create them
- how will they be useful

In short, **libraries** are a set of built-in functions, constant and header files, gathered into one place.

Gather useful functions.

How to retrieve a program's arguments.

Conditional, so we don't have to recompile every time we want it to have a different behavior.

## Librairies

Les librairies
```c
int 	main()
{
}
```
```sh
ls -la
emacs main.c
gcc main.c
gcc main.c ft_putstr.c ft_putchar.c
./a.out
gcc ft_putstr.c
gcc -c ft_putstr.c
ls -la
cat ft_putstr.o
# .o are the bricks of the wall that is the program
gcc -c ft_putchar.c
gcc -c main.c
gcc main.o ft_putstr.o ft_putchar.o
rm main.o
ls -la
ar rc libstr.a ft_putchar.o ft_putstr.o
ls -la
```
retomar @ 04:30
## Main's argument (argc, argv)

```c

```
# PISCINE C - DAY 07
## Compilation's steps

```c

```
## Dynamic memory allocation

```c

```
# PISCINE C - DAY 08
## Preprocessing - Introduction

```c

```
## Preprocessing - #include

```c

```
## Preprocessing - file.h

```c

```
## Preprocessing - #define

```c

```
## Preprocessing - #ifdef/#ifndef

```c

```
## Preprocessing - Multiple inclusions

```c

```
## Data structures - Typedef

```c

```
## Data structures - Struct

```c

```
## Data structures - Enum

```c

```
## Data structures - Union

```c

```
# PISCINE C - DAY 10
## Day 10 Introduction

```c

```
## Compilation Problematic

```c

```
## Makefile - Introduction

```c

```
## Makefile - Rules

```c

```
## Makefile - Variables

```c

```
## Makefile - Example

```c

```
## Pointers to functions - Introduction

```c
int x;
int *y;

x = 42;
y = &x;

*y = 0;

```
## Pointers to functions - Syntax

```c

```
## Pointers to functions - Example

```c

```
## Pointers to functions - Conclusion

```c

```
# PISCINE C - DAY 11
## Chained list - Introduction

```c

```
## Chained list - Examples

```c

```
## Chained list - Tips

```c

```
# PISCINE C - DAY 12
## Files - Introduction

```c

```
## File manipulation - Open

```c

```
## File manipulation - Write

```c

```
## File manipulation - Read

```c

```

```c

```

## File manipulation - Lseek
