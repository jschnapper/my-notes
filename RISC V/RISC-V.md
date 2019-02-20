# RISC-V
An Assembly language program

## Basics
* instructions are the primitive operations that a CPU may execute, done so in sequence
* different CPUs implement different sets of instructions. The set of instructions implemented by a CPU is called an **Instruction Set Architecture (ISA)**
  * ex: Intel x86 (i9, i7, i5...); RISC-V (the simpler language) 


5 parts to a computer
* Processor
  * (1) control
  * (2) Datapath
    * PC
    * Registers
    * Arithmetic & Logic Unit (ALU)
* (3) Memory
* (4) Input
* (5) Output 


## RISC
* Reduced Instruction Set Computing
* Keep instructions small and simple -- making it easier to build fast hardware
* Let the software do complicated operations by composing simpler ones

This classes using the 32-bit variant while the textbook covere 64-bit

## Assembly Variables and Register
* Assembly cannot use variables
* registers are SUPER fast 
* **Registers**: on the chip, on the cpu, in the processor, it's storage -- Assembly operands are **registers**
* Operations performed on registers -- all operands on the registers, not memory 
* registers have no type
* Because registers are hardware, there is a predetermined number of them
  * 32 in RISC-V
    * numbered 0 to 31
    * referred to as x0 - x31 (but can drop the x in conversation when saying "Register")
      * x0 is special and always holds 0
      * so only 31 registers available
    * Can be referred to by number or name
  * Each register is 32 bits wide (in RV32 variant)
  * groups of 32 bits = **word** in RV32  

## Assembly Instructions
* Each statement (called an **instruction**), executes exactly one of a short list of simple commands
* Each instruction is 32 bits
  
## Syntax
* comments are `#`
* rigid syntax: 1 operator, 3 operands 

One    two, three, four 
```
add x1, x2, x3
```
One = operation name
two = operand getting result (destination)
three = 1st operand for operation (source1)
four = 2nd operand for operation (source2)

**Spill** occurs when run out of registers and have to use memory -- don't want this top happen 

### Immediates
* Immediate: numerical constants
* There is no subtract immediate
  * Must use **signed bits** in order to negate constants  
  * used addi with a negative (can be down by compiler of user authoring code)
Operation register register constant
```addi x3, x4, 10```
Which is equivalent to C:
```f = g + 10```

### Register Zero
* hard-wire and cannot be changed
* it is always 0
This is not an error, but it will do nothing:
```add x0, x3, x4``` 

## Data Transfer
**Load from** (read data) and **store to** (write data) memory 
* Little-Endian

## Memory
* Memory addresses are in bytes
* 1 byte = 8 bits
* 1 word = 4 bytes = 32 bits
* Word addresses are 4 bytes apart
  * **Little Endian**: the rightmost bytes (least significant) is the address -- *RISC-V uses this*
    * ex: 1024 => 00000000 00000000 00000100 00000001
  * **Big Endian**: leftmost byte is the address  
    * ex: 1024 => 00000001 00000100 00000000 00000000
* Registers are 100 to 500 times faster than DRAM (Memory)
### Load from Memory to Register (word)
In C
```C
int A[100];
g = h + A[3]
```
In RISC-V
There is no declaration, so no conversion for `int A[100]`
Using `Load Word(lw)`
```
lw x10, 12(x15)  # x10 gets A[3]
add x11, x12, x10 # g = h + A[3]

```
`x15` - base register (pointer to `A[0]`)
`12` - offset in bytes
**Offset must be a constant known at assembly time**

**Date flow from right to left**

### Store from Register to Memory (word)
C code
```c
int A[100]
A[10] = h + A[3]
```
In RISC-V using Store Word `sw`
```
lw x10, 12(x15) # temp reg x10 gets A[3]
add x10, x12, x10 # temp reg x10 gets h + A[3]
sw x10, 40(x15) # A[10] = h + A[3];
```
`x15` = base register
`12,40` = offsets in bytes
`x15 + 12` and `x15 + 40` must be multiples of 4 because integer is 4 bytes
* this means that x15 can be off-aligned, but if offset compensate such that the sum is multiple of 4, it will work
**Date flow from left to right**

### Loading and Storing Bytes
byte data transfer:
load byte: `lb`
store byte: `sb`
Same foramte as `lw` and `sw` 
Does not need to be word aligned -- does not need to be  multiples of 4

**Copy to the lowe byte position**: the first byte

`lb` is **sign-extended**. The most signifcant bit is copied to fill the entire 32 bits of the register. 

RISC-V also has unsigned byte loads (`lbu`) which **zero extends** to fill the 32 bits of the register. There is no `sbu`.

## Decision Making
There are labels: L1 some line of code
`beq` branch if equal
`bne` branch if not equal
`beq register1, register2, L1`
if register1 == register, go to L1,
otherwise go to next statement

### Branches
2 kinds 
**Conditional Branch**: change control flow depending on outcome of comparison
* branch if equal, branch if not equal
* branch if less than (blt) branch if greather than or equal (bge)
* signed and unsigned values matter, must know what dealing with

**Unconditional Branch**: always branch
* in RISC-V: jump(j) as in `j label`
  * jump to another line, useful for jumping an else case

