# C

### Printing
```c
#include <stdio.h>
main()
{
  printf("hello, world\n");
}
```

Can format `printf` with arguments. Each `%` represents an argument in order, and **must match by number and type**

```c
printf("%d\t%d\n", fahr, celsius)
```
Th `%d` specifies an integer while `\t` and `\n` format tab and new line respectively. A signed value. Adding numbers adds width.`%3d` right justifies the number and occupies a field 3 digits wide.

If using float, use `%f`. For accuracy, precede with `.0f` which indicates how many digits after the decimal to include. In this case, it is 0 and won't include the decimal. 

`printf` is not part of C. There is not input or output in C. `printf` is a function from the standard library of functions normally accessible to C programs.

Use `%x` for hexadecimal, `%s` for string, `%c` for character

`%p` address of pointer 


### Compiling
Use a compiler to compile `program.c` into an executable that can be run like so `./a.out`. In CS61C we use `gcc` to compile, which has the command line option `-o` to name the executable.

compile
```c
/* compile */
gcc -o program program.c 

/* run */
./program
```

### C format and defaults

**While, for, conditionals** can be multi-line with `{...}` or single lines following the statement without brackets

Integer division is *truncacted*. 5/9 = 0.

An integer and float arithmetic sequence will convert the integer to a float. 

**Meaningful Values**
If a certain 

carries valuable meaning, don't hide it. Create **symbolic constants**:
```c
#define NAME replacement text
/* to be used as such*/
int x = NAME;
```
* these are not variables,so they do not appear in declarations
* they can be numbers or characters 
* there is not semi-colon


A return value of 0 in `main` implies normal termination while a return value of nonzero number implies an error.

0 is the only false value.

***C uses call by value*** -- the value of an argument is copied in a function rather than passing the original variable.

**Local Variables** are also called **Automatic Variables**

External, global variables ***must be defined*** in order to be accessed.





### Character Input Output,Strings and Character Arrays 
* text input and output is dealt as a stream of characters
* A **text stream** is a sequence of characers divided into lines
* each line has 0 or more characters and is followed by a newline character

`getchar()` returns next character in stream
`putchar(c)` prints the given character 

As soon as there are no more characters to get, `getchar()` returns `EOF`

`'A'` returns the ASCII value of the character -- it is a character constant, the integer value

A **String** is an array of characters. A string's internal representation is terminated with the character `\0`, thus it's length in storage is actually +1 character than what is observable, but that does not affect the length. The end of a string is indicated by this null when being parsed.

`char *a = "foobar";` is a string literal, so it is of length 6

`strcpy(s,t)` copies string t to s

`strcmp(s,t)` compares character strings s and t, returns negative, zero, or positive is s is lexiccographically less than, equal to, or greater than t.

```c
char amessage[] = "this potato";
char *pmessage = "this potato"
```
`amessage` is an array with the exact amount of memory allocated to it. The characters can change, but the memory will stay the same.

`pmessage` is a pointer to a string constant. It can be modified to point elsewhere, but the result is undefined if you try to modify the string contents

### Bitwise Operators
Can only be applied to integral operands: *char, short, int, and long* whether signed or unsigned.

`&` AND
`|` inclusive OR
`^` exclusive OR
`<<` left shift
`>>` right shift
`~` one's complement (unary)

`&` is used to mask off some set of bits
```c
/*sets to zero all but the low-order 7 bits of n*/
n = n & 0177;
```
Given two bits, when both are 1, copy that bit. 
```c
int a = 60 /*0011 1100*/
int b = 13 /*0000 1101*/
c = a & b  /*0000 1100*/ 
```



`|` turns bits on
```c
/* sets to one in x the bits that are set to one in SET_ON */
x = x | SET_ON
```
Given two bits, when either or both are 1, copy to 1.
```c
int a = 60 /*0011 1100*/
int b = 13 /*0000 1101*/
c = a & b  /*0011 1101*/ 
```

`^` sets a one in each bit position where its operants have different bits, and a zero where they are the same.

Given two bits, when one of them has a 1, copy that bit.
```c
int a = 60 /*0011 1100*/
int b = 13 /*0000 1101*/
c = a & b  /*0011 0001*/ 
```

More examples:
if `x` is 1 and `y` is 2, `x & y` is **zero**.

`<<` and `>>` perform left and right shifts of their left operand by the number of bit positions given by the right operand, which must be positive.

`x << 2` shifts the value of x left by two positions, filling the vacated bits with 0. Right shifting unsigned will fill vacated with 0. Right shifting signed depends on the machine. 

Keeps the same number of bits. Any 1's that fall off are removed. 

`~` converts each 1 bit into a 0 bit and vice versa
```c
/* sets the last six bits of x to zero*/
x = x & ~077
```


### Memory
A machine has an array of consecutively numbered or addressed memory cells that may be manipulated individually or in contiguous groups.

Two adjacent one-byte cells = **Short Int**

Four adjacent one-byte cells = **Long Int**

Often in groups of two or four and accessed with pointers.

**3 pools of memory**
* Static Storage: global variable storage, basically permanent, entire program run, does not grow or shrink
* The Stack: the local variable storage, parameters, return address (location of "activation records" in Java or "stack frame" in C). Grows down.
  * A lot of recursion: very little heap but a lot of stack
  * a large local array = large stack
* The Heap (dynamic malloc storage): data lives until deallocated by programmer. resizes dynamically, grows up
  * A large linked list has a large heap and small stack
  * Photoshop has a large heap and small stack. Ex: I want an image that will be 1000px by 1000px -- that is dynamically created space

... something prevents the heap and stack from overalapping -- will get to this

Variables declared **outside** a procedure (global), allocated in *static*

Variables declared **inside** procedure (local) allocated on the *stack* and **freed when procedure returns**
* `main()` is a procedure

**The Stack**
***Last in, first out***
Each of stack is divided into frames. Each frame includes
* Return "instruction" address (how to return to parent)
* parameters
* space for other local variales

Stack frames are contiguous blocks of memory.

**Stack Pointer** tells where bottom of stack frame is, and then moves down as frames grow to keep track of the bottom. The "top" of the stack is the first procedure: main. Stack pointer moves up as the frames are returned. 

**Every function call** takes stack space

When a procedure ends, the stack frame is tossed off the stack, freeing memory for the future stack frames.

Memory is managed automatically

**The Heap**
Large pool of memory, *not* allocated in contiguous order (i.e. back to back requests to heap may live in different places)

Specify the numer of **bytes** of memory explicitly to allocate item.

Memory is allocated and deallocated -- **must be managed**

**Avoid Fragmentation** (external fragmentation) -- which is when most of free memory is in many small chunks
* Might have many free bytes, but because the free bytes are not in contiguous memory, do not have enough space
* Heap has access to entire block, but doesn't necessarily assign in order. And when a space is freed, the other blocks don't slide into the freed space. This can lead to fragmentation.


### Pointers
* A pointer is an address represented as an unsigned value. 
* A pointer "points" to a group of cells (often in groups of two or four), holding an address for that group. 
* A pointer is a variable. 
* Why use pointers? Because FAST.

Declare pointer with `*`

If declare pointer without defining, then the address is random. **BAD**. Because if you then define after declaring, it is stored in a random location. 
**DONT DO THIS**
```c
/*bad*/
int *p;
p = 5
```

Get address of something with `&`. This is the right way to define the pointer. `&` only points to objects in memory (variables and arrays, NOT expressions or constants, etc.). `*` is then overridden and can be used to get the value, accessing the object the pointer points to. Now is called a *dereference operator*
```c
int *p, x;
x = 3;
/* gets the address of x */
p = &x 
/* prints value at the address */
printf("p points to %d\n", *p)
```
**Assign pointers to addresses, not values**
* once the address assigned, can reassign the value at the address directly `*p = 8`, which also changes the value of the variable that p points to

functionality: can use a function to change a value with pointers to bypass "call by value"

**Dangling reference**: use ptr before malloc
* pointer is pointer anywhere; it is written to random space in memory because being used before malloc
* the right way:
  * (1) allocate it
  * (2) set it equal to the malloc
  * (3) use it
  * (4) free it 


**Memory Leak**: tardy free, lose the ptr
* keep using more and more memory because not freeing it after using it 
* continue until no more space and malloc returns 0

### Arrays
* don't know own length
* bounds not checked
* Must pass the array and its size to any procedure 
* cannot ask for address of array; arrays are not variables -- thus cannot increment arrays like this either `a++`
  * however, an array by default is a pointer to the first element
Segmentation Faults: 
* writing to a place of memory that is not allowed/not supposed to be written to
* a place that memory was not reserved for

Bus Errors:
* could not transfer data onto the bus correctly 
* You're allowed to write to it, but you are not aligned
* Like if writing integers, but not accessing in multiple of 4 because of by some amount 


**malloc**: memory allocator
* speaks in pure raw bytes
* A contiguous memory promise
* allocate room for something to to point to
  * with help of typecase and sizeof

Reserves n contiguous integers. This allocates an array of n integers.
```c
ptr = (int *) malloc (n * sizeof(int));
```
`(int *)` tells compiler what will go into that space (Typecast)

Sometimes, the number is so big that malloc fails. So malloc should communicate when it fails/is full. *Returns null pointer, pointer to 0*. Malloc would never return 0 if it succeeds. 

**Therefore, every malloc call should say this**
`if ptr==0` and then handle the issue 

* once malloc() is called, the memory location contains garbage, so don't use it until set value
* after allocating, must free space:
  * `free(ptr)`

Things that can cause crash or behave strangely:
* freeing the same piece of memory twice
* calling free() on something you didn't get back from malloc()
* run time does not check for these mistakes 


`*` and `&` bind more tightly than arithmetic operators

```c
/* increments what p points to*/
++*p

/* increments the pointer itself along the array*/
*p++

/* increments what p points to*/
(*p)++

```

### Struct
A data structure composed fo simpler data types

Like a class in Java/C++ but without methods or inheritance.

A way to wrap some variables 

`->` the arrow operator **dereferences and extracts a structure field with a single operator**. 

```c
/*These are equivalent*/
struct point *p;

printf("x is %d\n", (*p).x);
printf("x is %d\n", p->x);
```

Using `sizeof` depends on the compiler. 
```c
struct p {
  char x;
  int y;
}
```
If compiler is **word-aligning** then it will round to 8 bytes. If it **is okay with not being word-aligned** it can be 5 bytes.

When a structure is declared, it does not allocate memory

### Typedef
`typedef`
Tells C that you are defining a new type 

### Global variables
Any data declared outside of any procedure (before `main`) has the global scope.


### Malloc, Free, and Heap Memory Management
* Each block of memory is preceded by a header that has two fields:
  * **size** of the block
  * **pointer** to the next block
* All **free blocks** are kept in a circular linked list (***A free list***). The pointer field is unused in an allocated block


`malloc` procedure:
* searches free list for a block that is big enough
* If none found, more memory requested from OS
* fails if not satisfied
* Malloc can be really slow because it has to check each sliver of the free list 
* How does malloc choose when multiple free blocks:
  * **best-fit**: choose the smallest block that is big enough for the request
    * goes through the whole list 
  * **first-fit**: choose the first block we see that is big enough
    * starts at beginning of list
    * be fast
  * **next-fit**: like first-fit but remember where we finished searching and resume searching from there 

`free` procedure:
* checks if the blocks adjacent to the freed block are also free
* If free, adjacent free blocks are merged (*coalesced*) into a single, larger free block
* Otherwise, the freed block is just added to the free list












